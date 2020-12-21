# sistema-eletrico-Lopez-M

-- phpMyAdmin SQL Dump
-- version 5.0.2
-- https://www.phpmyadmin.net/

--
-- Base de datos: `empresa_electrica`
--

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `clientes`
--

CREATE TABLE `clientes` (
  `cedula_cliente` int(11) NOT NULL,
  `nombres` varchar(50) DEFAULT NULL,
  `apellidos` varchar(50) DEFAULT NULL,
  `telefono` int(11) DEFAULT NULL,
  `sector_vive` varchar(40) DEFAULT NULL,
  `desc_convenio` varchar(5) DEFAULT NULL,
  `id_pagopk` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `clientes`
--

INSERT INTO `clientes` (`cedula_cliente`, `nombres`, `apellidos`, `telefono`, `sector_vive`, `desc_convenio`, `id_pagopk`) VALUES
(120444111, 'Edison', 'Real', 9123456, 'Tarqui', 'si', 3),
(121863736, 'Lucila', 'Macias', 9765432, 'La paz', 'si', 4),
(122987633, 'Melanie', 'Vera', 90909776, 'San pedro', 'si', 4),
(123097262, 'Roberto', 'Garcia', 91231523, 'Calle 13', 'si', 4),
(124097938, 'Carlos', 'gomez', 91989767, 'Las cumbres', 'si', 3);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `descripcion_pago`
--

CREATE TABLE `descripcion_pago` (
  `id_pago` int(11) NOT NULL,
  `nombre_mes` varchar(20) DEFAULT NULL,
  `aÃ±o` varchar(10) DEFAULT NULL,
  `nombre_pago` varchar(20) DEFAULT NULL,
  `total` decimal(6,2) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `descripcion_pago`
--

INSERT INTO `descripcion_pago` (`id_pago`, `nombre_mes`, `aÃ±o`, `nombre_pago`, `total`) VALUES
(1, 'Enero', '2018', 'paga', '50.00'),
(2, 'Febrero', '2018', 'paga', '70.00'),
(3, 'Marzo', '2018', 'Deuda', '50.00'),
(4, 'Marzo', '2018', 'paga', '78.00');

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `detallefacturas`
--

CREATE TABLE `detallefacturas` (
  `num_factura` varchar(20) NOT NULL,
  `total_convenio` decimal(6,2) DEFAULT NULL,
  `alumbrado_publico` decimal(6,2) DEFAULT NULL,
  `cuerpo_bombero` decimal(6,2) DEFAULT NULL,
  `basura` decimal(6,2) DEFAULT NULL,
  `cedula_clientepk` int(11) DEFAULT NULL,
  `cedula_empleadopk` int(11) DEFAULT NULL,
  `RUCpk` int(11) DEFAULT NULL,
  `numero_medidorpk` varchar(15) DEFAULT NULL,
  `id_facturapk` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `detallefacturas`
--

INSERT INTO `detallefacturas` (`num_factura`, `total_convenio`, `alumbrado_publico`, `cuerpo_bombero`, `basura`, `cedula_clientepk`, `cedula_empleadopk`, `RUCpk`, `numero_medidorpk`, `id_facturapk`) VALUES
('12345', '12.00', '3.00', '4.00', '3.00', 124097938, 131928393, 1234567, '1231', 1234),
('123456', '11.00', '2.00', '3.00', '3.00', 120444111, 131928393, 1234567, '1234', 2),
('987654', '14.00', '1.00', '3.00', '1.00', 121863736, 131928393, 1234567, '2570', 3);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `empleados`
--

CREATE TABLE `empleados` (
  `cedula_empleado` int(11) NOT NULL,
  `nombre` varchar(20) DEFAULT NULL,
  `apellido` varchar(20) DEFAULT NULL,
  `telefono` int(11) DEFAULT NULL,
  `direccion_e` varchar(40) DEFAULT NULL,
  `fecha_ing` date DEFAULT NULL,
  `RUCpk` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `empleados`
--

INSERT INTO `empleados` (`cedula_empleado`, `nombre`, `apellido`, `telefono`, `direccion_e`, `fecha_ing`, `RUCpk`) VALUES
(131928393, 'Luis', 'Perez', 68473898, 'San pedro', '2019-12-01', 1234567),
(1301728273, 'Pedro', 'Gomez', 2608927, 'Colorado', '2018-12-01', 1234567);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `empr_electrica`
--

CREATE TABLE `empr_electrica` (
  `RUC` int(11) NOT NULL,
  `nombre` varchar(20) DEFAULT NULL,
  `direccion` varchar(50) DEFAULT NULL,
  `telefono` int(11) DEFAULT NULL,
  `correo` varchar(50) DEFAULT NULL,
  `sitioweb` varchar(50) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `empr_electrica`
--

INSERT INTO `empr_electrica` (`RUC`, `nombre`, `direccion`, `telefono`, `correo`, `sitioweb`) VALUES
(1234567, 'Facci_electric', 'aven. circuvalacion', 2577026, 'facci_electric@hotmail', 'facci_electric.com');

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `facturap`
--

CREATE TABLE `facturap` (
  `id_factura` int(11) NOT NULL,
  `fecha_pago` date DEFAULT NULL,
  `total_pago` decimal(6,2) DEFAULT NULL,
  `num_facturapk` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `facturap`
--

INSERT INTO `facturap` (`id_factura`, `fecha_pago`, `total_pago`, `num_facturapk`) VALUES
(1234, '2018-03-03', '45.00', '12345');

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `medidores`
--

CREATE TABLE `medidores` (
  `numero_medidor` varchar(15) NOT NULL,
  `consumo_luz` varchar(10) DEFAULT NULL,
  `numero_lote` varchar(10) DEFAULT NULL,
  `cedula_empleadopk` int(11) DEFAULT NULL,
  `cedula_clientepk` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Volcado de datos para la tabla `medidores`
--

INSERT INTO `medidores` (`numero_medidor`, `consumo_luz`, `numero_lote`, `cedula_empleadopk`, `cedula_clientepk`) VALUES
('1231', '564kb', '14', 1301728273, 120444111),
('1234', '234kb', '13', 131928393, 124097938),
('1456', '423kb', '16', 1301728273, 121863736),
('17', '777kb', '17', 131928393, 122987633);

--
-- Ãndices para tablas volcadas
--

--
-- Indices de la tabla `clientes`
--
ALTER TABLE `clientes`
  ADD PRIMARY KEY (`cedula_cliente`),
  ADD KEY `id_pagopk` (`id_pagopk`);

--
-- Indices de la tabla `descripcion_pago`
--
ALTER TABLE `descripcion_pago`
  ADD PRIMARY KEY (`id_pago`);

--
-- Indices de la tabla `detallefacturas`
--
ALTER TABLE `detallefacturas`
  ADD PRIMARY KEY (`num_factura`),
  ADD KEY `cedula_clientepk` (`cedula_clientepk`),
  ADD KEY `cedula_empleadopk` (`cedula_empleadopk`),
  ADD KEY `RUCpk` (`RUCpk`),
  ADD KEY `numero_medidorpk` (`numero_medidorpk`);

--
-- Indices de la tabla `empleados`
--
ALTER TABLE `empleados`
  ADD PRIMARY KEY (`cedula_empleado`),
  ADD KEY `RUCpk` (`RUCpk`);

--
-- Indices de la tabla `empr_electrica`
--
ALTER TABLE `empr_electrica`
  ADD PRIMARY KEY (`RUC`);

--
-- Indices de la tabla `facturap`
--
ALTER TABLE `facturap`
  ADD PRIMARY KEY (`id_factura`),
  ADD KEY `num_facturapk` (`num_facturapk`);

--
-- Indices de la tabla `medidores`
--
ALTER TABLE `medidores`
  ADD PRIMARY KEY (`numero_medidor`),
  ADD KEY `cedula_empleadopk` (`cedula_empleadopk`),
  ADD KEY `cedula_clientepk` (`cedula_clientepk`);

--
-- Restricciones para tablas volcadas
--

--
-- Filtros para la tabla `clientes`
--
ALTER TABLE `clientes`
  ADD CONSTRAINT `clientes_ibfk_1` FOREIGN KEY (`id_pagopk`) REFERENCES `descripcion_pago` (`id_pago`);

--
-- Filtros para la tabla `detallefacturas`
--
ALTER TABLE `detallefacturas`
  ADD CONSTRAINT `detallefacturas_ibfk_1` FOREIGN KEY (`cedula_clientepk`) REFERENCES `clientes` (`cedula_cliente`),
  ADD CONSTRAINT `detallefacturas_ibfk_2` FOREIGN KEY (`cedula_empleadopk`) REFERENCES `empleados` (`cedula_empleado`),
  ADD CONSTRAINT `detallefacturas_ibfk_3` FOREIGN KEY (`RUCpk`) REFERENCES `empr_electrica` (`RUC`),
  ADD CONSTRAINT `detallefacturas_ibfk_4` FOREIGN KEY (`numero_medidorpk`) REFERENCES `medidores` (`numero_medidor`);

--
-- Filtros para la tabla `empleados`
--
ALTER TABLE `empleados`
  ADD CONSTRAINT `empleados_ibfk_1` FOREIGN KEY (`RUCpk`) REFERENCES `empr_electrica` (`RUC`);

--
-- Filtros para la tabla `facturap`
--
ALTER TABLE `facturap`
  ADD CONSTRAINT `facturap_ibfk_1` FOREIGN KEY (`num_facturapk`) REFERENCES `detallefacturas` (`num_factura`);

--
-- Filtros para la tabla `medidores`
--
ALTER TABLE `medidores`
  ADD CONSTRAINT `medidores_ibfk_1` FOREIGN KEY (`cedula_empleadopk`) REFERENCES `empleados` (`cedula_empleado`),
  ADD CONSTRAINT `medidores_ibfk_2` FOREIGN KEY (`cedula_clientepk`) REFERENCES `clientes` (`cedula_cliente`);



Cosultas
-
--La empresa necesita saber que clientes están al dia

select id_pago,nombres,apellidos,sector_vive,nombre_mes,aano,nombre_pago,total from clientes
   join descrpago on id_pago=id_pagopk where nombre_pago='Pagado' order by nombres asc;

-

--La empresa necesita saber los clientes que están en deuda

select id_pago,nombres,apellidos,sector_vive,nombre_mes,aano,nombre_pago,total from clientes
   join descrpacion_pago on id_pago=id_pagopk where nombre_pago='deuda' order by nombres asc;

-

--Se desea saber el valor del convenio que tiene cada cliente

select nombres,apellidos,sector_vive,total_convenio from detallefacturas join clientes on cedula_cliente=cedula_clientepk order by nombres asc 

-
--se desea sber que clientes consumes mas energía eléctrica

select numero_medidor,nombres,apellidos,sector_vive,consumo_luz,numero_lote from medidores 
        join clientes on cedula_cliente=cedula_clientepk where consumo_luz '200kb' order by nombres asc 

