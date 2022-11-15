# BdLocadora

```
-- phpMyAdmin SQL Dump
-- version 5.2.0
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Tempo de geração: 09-Nov-2022 às 16:00
-- Versão do servidor: 10.4.25-MariaDB
-- versão do PHP: 8.1.10

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Banco de dados: `locadora`
--

-- --------------------------------------------------------

--
-- Estrutura da tabela `cliente`
--

CREATE TABLE `cliente` (
  `id_cliente` int(11) NOT NULL,
  `cpf` varchar(14) NOT NULL,
  `nome` varchar(155) NOT NULL,
  `endereco` varchar(255) NOT NULL,
  `data_nasc` date NOT NULL,
  `telefone` varchar(15) NOT NULL,
  `email` varchar(55) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Extraindo dados da tabela `cliente`
--

INSERT INTO `cliente` (`id_cliente`, `cpf`, `nome`, `endereco`, `data_nasc`, `telefone`, `email`) VALUES
(1, '001.003.004-45', 'Adalto Jr', 'Rua da forca, 33', '0000-00-00', '(85) 32904456', 'car@gmail.com');

-- --------------------------------------------------------

--
-- Estrutura da tabela `clientes_has_filmes`
--

CREATE TABLE `clientes_has_filmes` (
  `id_clientes_filmes` int(11) NOT NULL,
  `id_cliente` int(11) NOT NULL,
  `id_filme` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- --------------------------------------------------------

--
-- Estrutura da tabela `filmes`
--

CREATE TABLE `filmes` (
  `id_filme` int(11) NOT NULL,
  `nome` varchar(55) NOT NULL,
  `ano` year(4) NOT NULL,
  `duracao` time NOT NULL,
  `class_idade` int(11) NOT NULL,
  `id_genero` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Extraindo dados da tabela `filmes`
--

INSERT INTO `filmes` (`id_filme`, `nome`, `ano`, `duracao`, `class_idade`, `id_genero`) VALUES
(1, 'Como eu era antes de você', 2010, '01:40:00', 12, 3),
(2, 'Motoqueiro Fantasma', 2014, '02:30:00', 16, 1);

-- --------------------------------------------------------

--
-- Estrutura da tabela `generos`
--

CREATE TABLE `generos` (
  `id_genero` int(11) NOT NULL,
  `nome` varchar(55) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Extraindo dados da tabela `generos`
--

INSERT INTO `generos` (`id_genero`, `nome`) VALUES
(1, 'Ação'),
(2, 'Terror'),
(3, 'Romance');

--
-- Índices para tabelas despejadas
--

--
-- Índices para tabela `cliente`
--
ALTER TABLE `cliente`
  ADD PRIMARY KEY (`id_cliente`),
  ADD UNIQUE KEY `cpf` (`cpf`);

--
-- Índices para tabela `clientes_has_filmes`
--
ALTER TABLE `clientes_has_filmes`
  ADD PRIMARY KEY (`id_clientes_filmes`),
  ADD KEY `id_cliente` (`id_cliente`),
  ADD KEY `id_filme` (`id_filme`);

--
-- Índices para tabela `filmes`
--
ALTER TABLE `filmes`
  ADD PRIMARY KEY (`id_filme`),
  ADD KEY `id_genero` (`id_genero`);

--
-- Índices para tabela `generos`
--
ALTER TABLE `generos`
  ADD PRIMARY KEY (`id_genero`);

--
-- AUTO_INCREMENT de tabelas despejadas
--

--
-- AUTO_INCREMENT de tabela `cliente`
--
ALTER TABLE `cliente`
  MODIFY `id_cliente` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT de tabela `clientes_has_filmes`
--
ALTER TABLE `clientes_has_filmes`
  MODIFY `id_clientes_filmes` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT de tabela `filmes`
--
ALTER TABLE `filmes`
  MODIFY `id_filme` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=3;

--
-- AUTO_INCREMENT de tabela `generos`
--
ALTER TABLE `generos`
  MODIFY `id_genero` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- Restrições para despejos de tabelas
--

--
-- Limitadores para a tabela `clientes_has_filmes`
--
ALTER TABLE `clientes_has_filmes`
  ADD CONSTRAINT `clientes_has_filmes_ibfk_1` FOREIGN KEY (`id_cliente`) REFERENCES `cliente` (`id_cliente`),
  ADD CONSTRAINT `clientes_has_filmes_ibfk_2` FOREIGN KEY (`id_filme`) REFERENCES `filmes` (`id_filme`);

--
-- Limitadores para a tabela `filmes`
--
ALTER TABLE `filmes`
  ADD CONSTRAINT `filmes_ibfk_1` FOREIGN KEY (`id_genero`) REFERENCES `generos` (`id_genero`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;

```
