# Projeto-Final-SQL

--DDL - Criando tabelas
CREATE TABLE IF NOT EXISTS cliente (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    cpf TEXT NOT NULL UNIQUE,
    ativo BOOLEAN DEFAULT TRUE,
    data_criacao DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE IF NOT EXISTS conta (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    numero INTEGER NOT NULL UNIQUE,
    saldo REAL NOT NULL DEFAULT 0.00,
    ativo BOOLEAN DEFAULT TRUE,
    data_criacao DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE IF NOT EXISTS cliente_conta (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    id_cliente INTEGER REFERENCES cliente(id),
    id_conta INTEGER REFERENCES conta(id),
    dependente BOOLEAN DEFAULT FALSE,
    ativo BOOLEAN DEFAULT TRUE,
    data_criacao TIMESTAMP NOT NULL DEFAULT (datetime('now','localtime'))
);
CREATE UNIQUE INDEX id_cliente_conta_unicos ON cliente_conta (id_cliente, id_conta);

CREATE TABLE IF NOT EXISTS tipo_transacao (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    descricao TEXT NOT NULL UNIQUE,
    ativo BOOLEAN DEFAULT TRUE,
    data_criacao TIMESTAMP NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE IF NOT EXISTS transacao (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    id_tipo_transacao INTEGER REFERENCES tipo_transacao(id),
    id_cliente_conta INTEGER REFERENCES cliente_conta(id),
    valor DECIMAL NOT NULL,
    data_realizacao TIMESTAMP NOT NULL DEFAULT (datetime('now','localtime'))
);
DML BancoToti.sql
--DML - Adicionando cargas iniciais
INSERT INTO cliente (nome, cpf)
VALUES 
	('Alejandro Dario Centeno', '20806024941'),
	('Andrea Montoya', '92610698124'),
	('Danilson Nunes Dos Reis', '56010395739'),
	('Edwin Alexander Sanchez Delgado', '35132395197'),
	('Elluz Rodriguez', '98565489221'),
	('Francoise luzolo Valentine', '84940515874'),
	('Genesys Rondon', '25729819911'),
	('Isis Parra', '08313084976'),
	('Jose Alejandro', '27305229881'),
	('Juan Ignacio Rojo Maldonado', '57825158583'),
	('Julio Andres Montoya Ruiz', '18552445549'),
	('Karen Stephany Gallardo Ochoa', '93318874497'),
	('Karliana', '79915676551'),
	('Keiny Rivas', '07641145899'),
	('Luis Alberto Ruiz Gomez', '01366199049'),
	('Marianela Méndez', '50493197806'),
	('Nestor Graterol', '24397451945'),
	('Patrick Paul', '71417488061'),
	('Pedro Abreu Arenas', '02245587960'),
	('Robert Raimundo Garabán Garcías', '06355445985'),
	('Roselino José Alvarado Alvarado', '86070472238'),
	('Vaibhav Phuskele', '01663784107'),
	('Verónica Castillo', '67291590452'),
	('Wladimir Kochmansky', '28403957018'),
	('Yairo Jose Sanchez Querales', '02531095742'),
	('Marcelo (Pai)', '41513065132'),
	('Rosangela (Mãe)', '94516512513'),
	('Kauê', '01615152156'),
	('Mariah (irma)', '01321320354'),
    ('Filho A', '59336481149'),
	('Filho B', '66629269013'),
	('Filho C', '20079428826'),
	('Filho D', '50123854734'),
	('Filho E', '96757832268'),
	('Filho F', '82757766902')
    ;
INSERT INTO conta (numero)
VALUES
        ('1000001'),
        ('1000002'),
        ('1000003'),
        ('1000004'),
        ('1000005'),
        ('1000006'),
        ('1000007'),
        ('1000008'),
        ('1000009'),
        ('1000010'),
        ('1000011'),
        ('1000012'),
        ('1000013'),
        ('1000014'),
        ('1000015'),
        ('1000016'),
        ('1000017'),
        ('1000018'),
        ('1000019'),
        ('1000020'),
        ('1000021'),
        ('1000022'),
        ('1000023'),
        ('1000024'),
        ('1000025'),
        ('1000026'),
        ('1000027'),
        ('1000028'),
        ('1000029'),
        ('1000030');
INSERT INTO cliente_conta 
	(id_cliente, id_conta, dependente)
VALUES
	        ('1', '1', false),
        ('2', '2', false),
        ('3', '3', false),
        ('4', '4', false),
        ('5', '5', false),
        ('6', '6', false),
        ('7', '7', false),
        ('8', '8', false),
        ('9', '9', false),
        ('10', '10', false),
        ('11', '11', false),
        ('12', '12', false),
        ('13', '13', false),
        ('14', '14', false),
        ('15', '15', false),
        ('16', '16', false),
        ('17', '17', false),
        ('18', '18', false),
        ('19', '19', false),
        ('20', '20', false),
        ('21', '21', false),
        ('22', '22', false),
        ('23', '23', false),
        ('24', '24', false),
        ('25', '25', false),
        ('26', '26', true),
        ('27', '26', false),
        ('28', '28', false),
        ('29', '29', false),
        ('27', '30', false),
        ('28', '30', true),
        ('29', '30', true),
        ('27', '27', false),
        ('30', '13', true),
        ('31', '4', true),
        ('32', '20', true),
        ('33', '21', true),
        ('34', '20', true),
        ('35', '13', true);
INSERT INTO tipo_transacao
	(descricao)
VALUES
	('depósito'),
    ('saque'),
    ('pagar conta'),
    ('transferencia');
INSERT INTO transacao
	(id_tipo_transacao, id_cliente_conta, valor)
VALUES
                (1, 1, 62705.69),
        (1, 2, 38102.54),
        (1, 3, 28171.4),
        (1, 4, 45937.63),
        (1, 5, 67911.3),
        (1, 6, 46132.41),
        (1, 7, 96020.6),
        (1, 8, 83758.46),
        (1, 9, 8001.1),
        (1, 10, 55105.8),
        (1, 11, 64028.19),
        (1, 12, 14397.26),
        (1, 13, 79606.2),
        (1, 14, 74865.77),
        (1, 15, 82727.38),
        (1, 16, 4635.2),
        (1, 17, 87695.07),
        (1, 18, 18823.53),
        (1, 19, 17170.37),
        (1, 20, 99173.96),
        (1, 21, 40777.79),
        (1, 22, 75650.71),
        (1, 23, 49502.97),
        (1, 24, 36089.16),
        (1, 25, 28994.28),
        (1, 26, 75622.15),
        (1, 27, 57511.06),
        (1, 28, 1449.86),
        (1, 29, 29617.25),
        (1, 30, 97957.51),
        (1, 27, 856.21),
        (1, 3, 586.33),
        (1, 21, 307.12),
        (4, 14, 295.12),
        (3, 32, 196.35),
        (2, 20, 929.44),
        (3, 39, 663.3),
        (4, 4, 284.98),
        (3, 17, 839.07),
        (3, 3, 924.77),
        (2, 6, 50.33),
        (1, 39, 846.67),
        (4, 17, 45.34),
        (2, 22, 703.15),
        (2, 34, 211.3),
        (4, 38, 388.85),
        (4, 4, 882.06),
        (2, 26, 659.78),
        (1, 31, 589.38),
        (3, 12, 300.85),
        (2, 17, 149.19),
        (3, 13, 897.44),
        (1, 12, 804.25),
        (3, 34, 745.64),
        (3, 27, 411.18),
        (4, 18, 788.06),
        (4, 36, 842.73),
        (2, 20, 102.43),
        (2, 10, 614.07),
        (2, 30, 418.13),
        (4, 11, 270.66),
        (3, 18, 873.51),
        (4, 39, 116.04),
        (4, 17, 253.63),
        (4, 22, 423.74),
        (4, 34, 393.32),
        (4, 4, 530.82),
        (2, 1, 264.57),
        (2, 14, 964.83),
        (1, 31, 386.66),
        (4, 26, 228.13),
        (2, 9, 524.35),
        (3, 19, 148.92),
        (1, 31, 650.33),
        (2, 37, 577.09),
        (3, 30, 449.7),
        (1, 10, 409.77),
        (1, 24, 953.47),
        (4, 11, 466.3),
        (3, 1, 278.15),
        (1, 16, 68.07),
        (1, 26, 606.1),
        (4, 23, 523.6),
        (2, 37, 8.87),
        (3, 29, 266.03),
        (2, 13, 146.94),
        (2, 24, 565.01),
        (3, 9, 287.93),
        (4, 28, 449.53),
        (4, 25, 90.97),
        (4, 4, 377.65),
        (4, 9, 692.48),
        (2, 1, 903.47),
        (2, 35, 385.13),
        (3, 6, 985.15),
        (1, 13, 560.83),
        (2, 25, 999.05),
        (1, 16, 147.29),
        (1, 30, 57.03),
        (4, 12, 926.43),
        (3, 14, 934.22),
        (3, 32, 409.21),
        (4, 10, 104.73),
        (2, 19, 243.83),
        (3, 12, 838.75),
        (1, 4, 948.36),
        (4, 37, 557.39),
        (1, 35, 443.15),
        (2, 2, 175.68),
        (2, 36, 876.61),
        (4, 38, 729.17),
        (4, 12, 416.91),
        (1, 4, 398.45),
        (3, 5, 455.4),
        (2, 11, 77.91),
        (4, 16, 329.62),
        (3, 26, 820.82),
        (3, 4, 627.74),
        (1, 14, 11.06),
        (2, 26, 144.78),
        (1, 39, 621.81),
        (1, 15, 996.25),
        (4, 18, 820.18),
        (2, 10, 488.17),
        (3, 4, 843.17),
        (3, 25, 435.02),
        (4, 25, 119.3),
        (4, 1, 408.34),
        (4, 2, 139.52),
        (2, 8, 199.3),
        (1, 15, 424.99),
        (1, 38, 756.33),
        (1, 29, 913.89),
        (1, 14, 292.73),
        (3, 10, 247.4),
        (2, 27, 786.92),
        (3, 17, 311.99),
        (1, 6, 966.37),
        (2, 13, 262.07),
        (4, 8, 181.72),
        (4, 34, 358.1),
        (3, 37, 556.2),
        (3, 4, 800.72),
        (4, 18, 12.43),
        (4, 29, 293.8),
        (2, 5, 418.04),
        (4, 17, 37.44),
        (4, 25, 198.21),
        (4, 11, 928.01),
        (1, 11, 489.16),
        (3, 3, 852.7),
        (4, 1, 766.43),
        (3, 17, 522.26),
        (2, 26, 994.99),
        (1, 6, 433.3),
        (1, 35, 699.25),
        (2, 36, 420.08),
        (4, 14, 27.59),
        (4, 2, 209.67),
        (2, 37, 341.34),
        (2, 23, 282.48),
        (3, 20, 149.08),
        (1, 23, 745.35),
        (4, 2, 254.69),
        (2, 1, 413.57),
        (1, 15, 818.84),
        (1, 31, 674.29),
        (4, 38, 36.81),
        (1, 12, 251.3),
        (3, 21, 307.63),
        (4, 15, 732.27),
        (1, 24, 966.94),
        (1, 17, 657.83),
        (2, 35, 844.51),
        (4, 11, 347.35),
        (2, 10, 412.3),
        (3, 33, 172.26),
        (4, 33, 44.6),
        (3, 4, 142.28),
        (2, 22, 712.79),
        (2, 5, 885.68),
        (1, 5, 185.78),
        (2, 33, 57.81),
        (1, 22, 767.07),
        (1, 11, 64.21),
        (4, 12, 642.15),
        (2, 32, 631.62),
        (4, 6, 766.86),
        (4, 14, 80.26),
        (1, 5, 739.66),
        (4, 17, 260.88),
        (4, 11, 468.61),
        (2, 28, 615.72),
        (3, 19, 476.3),
        (3, 28, 39.77),
        (3, 4, 52.72),
        (3, 8, 472.57),
        (1, 38, 944.86),
        (2, 29, 994.13),
        (1, 21, 0.57),
        (1, 13, 667.63),
        (3, 37, 910.13),
        (1, 31, 236.28),
        (4, 5, 517.98),
        (4, 38, 797.21),
        (3, 15, 825.87),
        (1, 13, 731.23),
        (4, 5, 851.43),
        (2, 25, 936.28),
        (3, 26, 628.33),
        (1, 27, 3.99),
        (3, 27, 379.21),
        (1, 14, 583.52),
        (3, 14, 913.74),
        (3, 9, 223.38),
        (2, 39, 614.75),
        (4, 34, 379.45),
        (1, 28, 596.45),
        (2, 34, 673.59),
        (3, 28, 232.92),
        (1, 18, 509.59),
        (3, 37, 852.26),
        (2, 30, 668.2),
        (1, 39, 922.4),
        (4, 12, 857.67),
        (3, 11, 78.6),
        (3, 37, 474.3),
        (1, 13, 278.68),
        (1, 34, 96.33),
        (3, 10, 748.11),
        (3, 11, 795.87),
        (3, 33, 81.58),
        (3, 39, 993.03),
        (3, 15, 397.21),
        (1, 14, 815.45),
        (4, 10, 150.44),
        (3, 11, 269.14),
        (2, 22, 573.52),
        (1, 25, 712.46),
        (4, 20, 536.96),
        (3, 39, 377.9),
        (2, 39, 368.28),
        (2, 29, 963.97),
        (2, 18, 102.17),
        (1, 28, 564.33),
        (4, 7, 180.13),
        (2, 26, 590.21),
        (2, 10, 528.81),
        (1, 20, 535.96),
        (1, 29, 595.95),
        (1, 4, 832.45),
        (2, 26, 543.85),
        (3, 38, 7.73),
        (1, 2, 732.56),
        (3, 33, 544.62),
        (2, 27, 568.48),
        (3, 8, 287.78),
        (1, 7, 59.7),
        (4, 21, 842.79),
        (3, 28, 174.05),
        (2, 36, 942.9),
        (4, 31, 620.27),
        (2, 21, 288.3),
        (4, 33, 602.01),
        (1, 19, 423.36),
        (2, 38, 678.09),
        (3, 11, 80.11),
        (2, 13, 205.01),
        (2, 37, 336.11),
        (2, 4, 156.44),
        (1, 19, 401.25),
        (1, 20, 983.23),
        (4, 35, 834),
        (2, 38, 782.37),
        (1, 24, 201.87),
        (4, 8, 426.49),
        (1, 28, 335.56),
        (2, 4, 622.3),
        (1, 19, 307.51),
        (1, 21, 627.35),
        (2, 26, 505.7),
        (2, 38, 683.69),
        (1, 14, 817.07),
        (3, 31, 104.29),
        (1, 27, 112.24),
        (4, 2, 465.58),
        (4, 18, 298.07),
        (2, 38, 966.04),
        (2, 3, 26.69),
        (2, 8, 767.47),
        (3, 14, 300.29),
        (3, 17, 959.76),
        (3, 14, 259.52),
        (3, 10, 711.69),
        (1, 19, 189.74),
        (3, 25, 575.25),
        (4, 14, 511.13),
        (1, 15, 798.5),
        (2, 10, 255.41),
        (3, 13, 726.19),
        (4, 8, 279.18),
        (4, 39, 896.2),
        (3, 36, 460.03),
        (4, 39, 596.79),
        (1, 33, 91.57),
        (2, 24, 370.45),
        (4, 31, 93.97),
        (3, 8, 28.28),
        (1, 4, 930.85),
        (3, 20, 77.2),
        (4, 21, 947.62),
        (4, 14, 324.7),
        (3, 9, 382.38),
        (4, 6, 683.24),
        (4, 17, 442.89),
        (2, 34, 580.8),
        (4, 12, 472.49),
        (2, 34, 736.13),
        (3, 27, 458.53),
        (3, 8, 577.67),
        (3, 30, 566.57),
        (4, 31, 82.03),
        (2, 24, 346.43),
        (2, 26, 952.43),
        (2, 18, 69.1),
        (3, 23, 625.77),
        (1, 2, 867.67),
        (4, 17, 728.42),
        (1, 20, 8.2),
        (4, 10, 41.25),
        (3, 8, 477.29),
        (4, 38, 391.01),
        (2, 32, 897.08),
        (4, 35, 873.8),
        (4, 27, 555.61),
        (2, 19, 511.26),
        (1, 29, 543.01),
        (2, 10, 527.43),
        (2, 8, 821.62),
        (3, 39, 456.18),
        (1, 27, 721.52),
        (1, 29, 900.73),
        (1, 38, 270.56),
        (2, 11, 978.85),
        (1, 7, 849.26),
        (1, 32, 924.3),
        (4, 10, 552.79),
        (4, 11, 455.55),
        (4, 11, 973.77),
        (1, 38, 960.6),
        (2, 18, 755.19),
        (4, 34, 229.32),
        (2, 18, 551.36),
        (2, 30, 953.85),
        (4, 31, 58.83),
        (1, 16, 930.51),
        (1, 36, 606.75),
        (3, 26, 363.24),
        (1, 27, 728.35),
        (2, 18, 774.8),
        (2, 20, 958.64),
        (1, 11, 276.81),
        (3, 38, 338.33),
        (1, 35, 687.75),
        (2, 4, 255.17),
        (3, 15, 686.47),
        (2, 16, 61.34),
        (4, 34, 672.41),
        (2, 36, 591.41),
        (3, 5, 706.33),
        (1, 33, 229.58),
        (1, 34, 122.55),
        (1, 3, 478.11),
        (1, 16, 537.05),
        (4, 16, 238.76),
        (4, 17, 788.97),
        (4, 21, 896.87),
        (3, 8, 218.26),
        (1, 17, 188.02),
        (1, 3, 830.09),
        (1, 18, 111.28),
        (2, 14, 668.8),
        (4, 17, 443.59),
        (2, 36, 820.28),
        (2, 27, 807.08),
        (4, 28, 191.78),
        (2, 2, 576.53),
        (1, 32, 750.57),
        (4, 24, 6.33),
        (3, 8, 516.54),
        (4, 32, 856.52),
        (1, 21, 936.27),
        (4, 38, 41.42),
        (4, 35, 563.91),
        (1, 24, 683.65),
        (2, 8, 344.61),
        (3, 18, 684.48),
        (4, 3, 454.55),
        (3, 3, 9.25),
        (4, 31, 173.03),
        (1, 17, 305.76),
        (1, 9, 831.39),
        (1, 23, 934.47),
        (1, 34, 544.69),
        (2, 2, 681.91),
        (1, 39, 337.97),
        (2, 35, 281.68),
        (4, 23, 942.81),
        (4, 10, 790.83),
        (4, 24, 83.81),
        (3, 31, 9.08),
        (3, 35, 478.99),
        (4, 7, 614.15),
        (2, 34, 135.78),
        (3, 5, 882.78),
        (2, 2, 283.09),
        (1, 39, 622.07),
        (3, 13, 501.22),
        (3, 26, 833.32),
        (1, 21, 213.45),
        (2, 14, 236.94),
        (1, 38, 714.13),
        (4, 36, 905.02),
        (3, 18, 715.82),
        (2, 19, 163.24),
        (1, 38, 0.1),
        (3, 10, 656.83),
        (3, 9, 8.48),
        (2, 36, 30.75),
        (4, 3, 78.3),
        (4, 32, 292.19),
        (4, 32, 837.93),
        (2, 26, 326.29),
        (3, 19, 961.15),
        (2, 19, 683.13),
        (1, 29, 836.05),
        (3, 1, 86.48),
        (1, 15, 632.19),
        (1, 31, 810.45),
        (1, 15, 14.2),
        (4, 34, 289.61),
        (3, 22, 222.53),
        (3, 19, 966.6),
        (3, 18, 153.59),
        (1, 16, 319.48),
        (1, 28, 263.72),
        (3, 11, 362.46),
        (4, 9, 793.57),
        (3, 9, 277.25),
        (1, 13, 772.11),
        (2, 28, 541.19),
        (1, 19, 180.5),
        (3, 2, 289.46),
        (2, 10, 314.85),
        (4, 24, 234.44),
        (1, 3, 919.99),
        (1, 11, 301.29),
        (3, 38, 822.36),
        (4, 9, 995.82),
        (2, 22, 173.6),
        (3, 3, 153.44),
        (4, 26, 744.74),
        (3, 32, 115.99),
        (4, 17, 58.9),
        (1, 3, 19.73),
        (2, 38, 201.52),
        (2, 38, 961.06),
        (2, 12, 447.44),
        (1, 26, 529.15),
        (1, 8, 44.75),
        (1, 15, 982.52),
        (4, 33, 610.49),
        (3, 34, 112.29),
        (1, 31, 244.46),
        (1, 2, 222.28),
        (2, 11, 135.74),
        (3, 15, 296.34),
        (2, 23, 713.71),
        (2, 14, 180.12),
        (1, 15, 230.72),
        (3, 38, 826.45),
        (2, 10, 617.1),
        (4, 8, 423.73),
        (2, 31, 939.8),
        (2, 35, 613.09),
        (3, 9, 352.22),
        (2, 4, 302.77),
        (1, 10, 931.3),
        (2, 33, 595.99),
        (3, 10, 757.7),
        (4, 21, 578.77),
        (1, 10, 360.3),
        (3, 10, 674.74),
        (1, 15, 684.49),
        (1, 24, 701.62),
        (1, 25, 879.66),
        (2, 11, 884.55),
        (2, 35, 868.88),
        (2, 29, 850.77),
        (3, 39, 158.24),
        (2, 35, 992.59),
        (3, 35, 66.27),
        (1, 38, 716.34),
        (1, 38, 270.02),
        (1, 26, 656.36),
        (3, 36, 643.69),
        (4, 39, 319.76),
        (2, 16, 41.42),
        (4, 16, 219.81),
        (2, 14, 287.6),
        (2, 20, 968.23),
        (4, 22, 886.73),
        (3, 11, 126.62),
        (2, 36, 159.59),
        (3, 11, 699.5),
        (3, 37, 822.34),
        (2, 3, 801.82),
        (1, 6, 728.83),
        (4, 33, 305.05),
        (1, 11, 230.78),
        (2, 5, 693.81),
        (4, 24, 623.71),
        (4, 38, 220.03),
        (3, 17, 543.7),
        (1, 36, 978.63),
        (4, 5, 178.6),
        (1, 18, 237.3),
        (2, 14, 330.82),
        (1, 13, 206.27),
        (4, 39, 903.18),
        (2, 7, 140.22),
        (2, 30, 317.61),
        (2, 4, 916.29),
        (2, 11, 872.34),
        (2, 3, 955.95),
        (2, 3, 609.58),
        (3, 31, 965.46),
        (2, 32, 23.96),
        (1, 12, 605.51),
        (3, 26, 874.56),
        (3, 28, 995.01),
        (3, 35, 559.84),
        (3, 25, 271.33),
        (2, 8, 426.88),
        (1, 13, 118.17),
        (4, 29, 71.82),
        (1, 28, 815.45),
        (3, 11, 68.25),
        (4, 23, 531.02),
        (4, 18, 660.6),
        (3, 15, 63.01),
        (2, 19, 170.35),
        (3, 19, 340.03),
        (4, 2, 179.14),
        (1, 23, 715.96),
        (3, 38, 832.42),
        (2, 8, 459.86),
        (1, 27, 815.4),
        (4, 7, 80.68),
        (1, 25, 14.87),
        (1, 12, 962.73),
        (1, 1, 530.99),
        (1, 2, 681.19),
        (3, 2, 335.71),
        (2, 27, 758.11),
        (4, 17, 392.85),
        (4, 5, 185.7),
        (4, 20, 721.86),
        (2, 3, 947.19),
        (1, 37, 574.22),
        (3, 21, 899.78),
        (1, 38, 330.66),
        (1, 36, 631.1),
        (2, 2, 759.35),
        (2, 26, 373.21),
        (1, 28, 99.57),
        (1, 38, 355.18),
        (2, 22, 862.99),
        (4, 24, 430.29),
        (2, 30, 943.02),
        (2, 12, 743.92),
        (3, 2, 371.2),
        (2, 26, 164.74),
        (4, 2, 995.35),
        (2, 19, 221.5),
        (2, 37, 224.54),
        (2, 38, 140.86),
        (2, 21, 397.31),
        (1, 1, 23.02),
        (1, 18, 997.32),
        (1, 2, 211),
        (1, 24, 941.1),
        (3, 3, 979.33),
        (4, 1, 178.62),
        (3, 19, 997.7),
        (1, 10, 424.9),
        (4, 21, 805.77),
        (2, 23, 631.3),
        (4, 5, 194.82),
        (2, 19, 822.95),
        (1, 19, 840.85),
        (3, 2, 794.23),
        (4, 38, 417.42),
        (3, 6, 350.57),
        (3, 15, 365.32),
        (1, 9, 901.29),
        (3, 11, 374.07),
        (2, 5, 196.24),
        (2, 35, 785.7),
        (1, 29, 417.28),
        (2, 22, 647.93),
        (1, 32, 103.68),
        (4, 12, 88.14),
        (2, 4, 36.32),
        (3, 11, 354.32),
        (3, 7, 116.94),
        (3, 12, 59.42),
        (4, 8, 952.8),
        (2, 16, 392.89),
        (4, 37, 650.11),
        (1, 1, 831.52),
        (3, 15, 697.73),
        (2, 4, 931.18),
        (2, 4, 610.58),
        (2, 15, 334.34),
        (1, 35, 635.19),
        (4, 30, 144.39),
        (4, 5, 590.96),
        (3, 12, 238.43),
        (1, 21, 234.17),
        (4, 29, 92.13),
        (3, 31, 149.74),
        (4, 31, 935.22),
        (3, 9, 470.16),
        (4, 5, 938.84),
        (3, 21, 924.14),
        (3, 6, 37.02),
        (2, 30, 168.94),
        (4, 27, 517.63),
        (2, 13, 761.34),
        (2, 19, 782.04),
        (3, 8, 782.01),
        (3, 31, 500.85),
        (3, 20, 215.06),
        (2, 18, 602.23),
        (3, 34, 978.05),
        (4, 9, 171.46),
        (2, 17, 634.64),
        (1, 6, 952.12),
        (2, 38, 549.75),
        (4, 29, 989.93),
        (2, 17, 672.24),
        (2, 1, 306.63),
        (1, 7, 467.77),
        (2, 19, 820.06),
        (2, 4, 351.12),
        (2, 6, 14.17),
        (2, 11, 465.7),
        (2, 6, 814.92),
        (2, 30, 874.28),
        (2, 13, 438.15),
        (4, 38, 310.23),
        (1, 20, 570.68),
        (2, 27, 107.42),
        (3, 29, 536.38),
        (1, 36, 900.14),
        (2, 9, 230.89),
        (1, 13, 143.99),
        (2, 34, 711.67),
        (1, 33, 545.53),
        (2, 28, 768.33),
        (1, 10, 552.29),
        (2, 23, 421.01),
        (2, 5, 205.66),
        (4, 26, 683.51),
        (4, 8, 815.93),
        (1, 10, 652.17),
        (3, 32, 109.18),
        (2, 35, 841.18),
        (2, 13, 108.69),
        (4, 39, 967.81),
        (2, 19, 44.74),
        (4, 28, 115.53),
        (2, 29, 893.42),
        (2, 32, 376.53),
        (2, 31, 693.22),
        (1, 12, 934.44),
        (2, 34, 902.25),
        (4, 1, 818.61),
        (4, 30, 674.16),
        (1, 5, 700.4),
        (3, 23, 841.11),
        (3, 11, 551.47),
        (2, 25, 499.88),
        (3, 22, 422.35),
        (3, 5, 666.96),
        (2, 21, 185.39),
        (4, 16, 369.9),
        (3, 16, 717.77),
        (2, 37, 509.17),
        (2, 38, 554.88),
        (2, 25, 696.07),
        (1, 9, 638.42),
        (3, 17, 249.43),
        (1, 32, 14.22),
        (3, 23, 426.02),
        (1, 20, 535.75),
        (1, 1, 435.3),
        (4, 38, 117.91),
        (2, 6, 627.56),
        (4, 37, 413.43),
        (3, 8, 582.6),
        (1, 22, 987.4),
        (1, 31, 411.24),
        (2, 23, 914.74),
        (2, 35, 20.47),
        (3, 30, 975.28),
        (1, 7, 101.29),
        (2, 22, 261.32),
        (1, 36, 250.13),
        (3, 6, 516.16),
        (2, 6, 616.64),
        (4, 23, 97.74),
        (1, 29, 324.73),
        (2, 32, 300.9),
        (3, 33, 294.51),
        (2, 8, 302.57),
        (4, 14, 12.51),
        (3, 11, 126.17),
        (2, 24, 878.29),
        (3, 31, 401.88),
        (2, 23, 478.91),
        (3, 21, 956.43),
        (1, 23, 99.18),
        (1, 27, 265.16),
        (3, 33, 916.02),
        (3, 36, 888.35),
        (4, 22, 208.22),
        (2, 22, 276.16),
        (3, 38, 958.54),
        (4, 32, 829.9),
        (2, 16, 960.43),
        (3, 4, 152.75),
        (2, 11, 855.57),
        (1, 25, 797.24),
        (1, 21, 917.4),
        (3, 37, 40.06),
        (3, 20, 215.96),
        (2, 10, 791.88),
        (4, 7, 517.47),
        (3, 13, 420),
        (1, 24, 712.57),
        (4, 11, 249.24),
        (3, 7, 164.36),
        (4, 24, 768.08),
        (2, 22, 416.69),
        (4, 19, 46.43),
        (3, 6, 605.8),
        (4, 4, 744.9),
        (3, 20, 438.91),
        (2, 38, 23.18),
        (1, 36, 112.92),
        (1, 35, 34.78),
        (1, 10, 276.3),
        (4, 21, 904.3),
        (1, 38, 428.95),
        (1, 36, 737.94),
        (3, 34, 708.15),
        (2, 16, 415.4),
        (4, 9, 132.84),
        (3, 9, 485.52),
        (1, 38, 243.67),
        (2, 30, 255.59),
        (3, 11, 958.75),
        (4, 22, 177.91),
        (2, 6, 4.94),
        (1, 17, 431.87),
        (3, 6, 726.68),
        (4, 28, 447.33),
        (2, 16, 526.93),
        (1, 38, 269.3),
        (2, 33, 872.39),
        (2, 13, 614.25),
        (2, 29, 273.95),
        (4, 38, 189.52),
        (2, 14, 116.78),
        (3, 15, 45.18),
        (1, 21, 708),
        (3, 39, 97.11),
        (3, 32, 585.08),
        (3, 17, 425.75),
        (1, 26, 499.15),
        (4, 26, 929.27),
        (2, 13, 675.73),
        (4, 16, 538.06),
        (1, 29, 942.02),
        (2, 15, 608.7),
        (4, 39, 186.75),
        (3, 14, 675.44),
        (2, 25, 834.72),
        (1, 27, 293.01),
        (3, 16, 634),
        (2, 25, 840.17),
        (2, 20, 987.51),
        (4, 8, 435.97),
        (3, 34, 341.56),
        (4, 37, 351.58),
        (2, 9, 158.69),
        (3, 21, 766.85),
        (2, 36, 748.39),
        (2, 21, 441.62),
        (3, 12, 563.62),
        (2, 18, 853.47),
        (4, 29, 458.63),
        (4, 21, 834.44),
        (1, 19, 170.21),
        (2, 17, 443.14),
        (2, 38, 864.71),
        (1, 5, 193.82),
        (4, 11, 780.36),
        (3, 28, 272.51),
        (2, 15, 692.65),
        (1, 24, 678.94),
        (4, 4, 401.79),
        (1, 21, 503.4),
        (4, 2, 558.55),
        (1, 4, 674.24),
        (2, 5, 638.05),
        (2, 35, 376.06),
        (2, 15, 583.06),
        (3, 15, 52.77),
        (4, 25, 767.44),
        (3, 37, 74.67),
        (3, 13, 287.45),
        (4, 14, 95.44),
        (3, 8, 841.93),
        (3, 3, 172.08),
        (2, 3, 390.28),
        (1, 21, 419.94),
        (2, 30, 517.86),
        (4, 23, 361.5),
        (1, 32, 738.28),
        (4, 15, 973.11),
        (4, 31, 428.18),
        (2, 5, 492.34),
        (1, 35, 437.55),
        (3, 10, 309.71),
        (1, 19, 723.77),
        (1, 33, 206.03),
        (4, 31, 303.34),
        (3, 30, 18.2),
        (2, 36, 947.36),
        (4, 10, 714.27),
        (2, 38, 17.13),
        (2, 35, 260.45),
        (3, 29, 658.47),
        (2, 34, 478.43),
        (2, 1, 868.72),
        (1, 2, 967.67),
        (4, 16, 201.38),
        (2, 32, 733.08),
        (4, 9, 669.36),
        (4, 30, 278.61),
        (2, 16, 700.71),
        (3, 31, 950.05),
        (1, 29, 348.62),
        (3, 15, 318.99),
        (4, 33, 780.03),
        (1, 9, 461.57),
        (1, 11, 893.06),
        (1, 24, 402.38),
        (1, 29, 629.03),
        (2, 34, 551.67),
        (1, 38, 649.18),
        (4, 10, 183.04),
        (4, 26, 893.36),
        (2, 17, 384.88),
        (1, 20, 596.15),
        (3, 12, 210.09),
        (2, 18, 428.54),
        (2, 31, 169.17),
        (4, 8, 995.39),
        (1, 9, 720.33),
        (2, 24, 245.69),
        (4, 24, 947.65),
        (2, 19, 844.82),
        (2, 19, 362.98),
        (1, 34, 981.34),
        (2, 28, 378.9),
        (4, 39, 804.67),
        (4, 38, 875.41),
        (4, 11, 947.7),
        (4, 33, 800.75),
        (2, 13, 719.88),
        (4, 26, 522.39),
        (3, 25, 261.67),
        (3, 37, 775.25),
        (1, 35, 540.76),
        (2, 19, 374.27),
        (3, 18, 712.4),
        (3, 38, 185.15),
        (4, 5, 339.12),
        (4, 6, 231.11),
        (3, 18, 906.8),
        (1, 21, 792.54),
        (2, 13, 231.52),
        (4, 13, 199.54),
        (4, 16, 831.23),
        (1, 4, 980.1),
        (3, 15, 353.92),
        (3, 19, 598.68),
        (3, 26, 284.85),
        (2, 21, 173.84),
        (4, 23, 584.15),
        (2, 26, 8.43),
        (1, 19, 676.34),
        (3, 5, 193),
        (4, 35, 478.95),
        (4, 34, 880.64),
        (4, 4, 430.54),
        (3, 2, 488.81),
        (2, 21, 881.48),
        (2, 4, 208.18),
        (3, 19, 725.14),
        (3, 10, 918.37),
        (1, 3, 863.53),
        (2, 29, 291.42);
DQLs de Exemplo BancoToti.sql
--DQL - Seleciona todos os clientes 
SELECT id, nome, cpf
FROM cliente;

--conta
SELECT id, numero, saldo 
FROM conta;

--cliente_conta
SELECT id, id_cliente, id_conta, dependente 
FROM cliente_conta;

--tipo_transacao
SELECT id, descricao
FROM tipo_transacao;

--transacao
SELECT id, id_tipo_transacao, id_cliente_conta, valor
FROM transacao;

SELECT id
FROM cliente
WHERE
    nome LIKE 'Kau%' ;
    

 
SELECT id, id_tipo_transacao, id_cliente_conta, valor
FROM transacao
WHERE
    (id_cliente_conta IN (1,2,3,4,5)
    AND valor > 5000)
    OR (id_cliente_conta IN (31,32,33,34,35)
    AND valor < 50);
    


SELECT
    id,
    COUNT(id) AS "Quantidade",
    SUM(valor) AS "Soma",
    MAX(valor) AS "Máximo",
    MIN(valor) AS "Mínimo",
    AVG(valor) AS "Média"
FROM transacao
GROUP BY id_tipo_transacao
ORDER BY 1;

SELECT
    transacao.id_tipo_transacao,
    descricao,
    COUNT(transacao.id) AS "Quantidade",
    SUM(valor) AS "Soma",
    MAX(valor) AS "Máximo",
    MIN(valor) AS "Mínimo",
    AVG(valor) AS "Média"
FROM transacao
JOIN tipo_transacao
	ON transacao.id_tipo_transacao = tipo_transacao.id
GROUP BY transacao.id_tipo_transacao, descricao
ORDER BY 1;



SELECT
    id, valor
FROM
    transacao
ORDER BY id DESC
LIMIT 5;



Consultas

1. Tem alguns Clientes que são dependentes. Quero que vocês me digam de que clientes eles são dependentes.
○ Por exemplo “Filho A” é dependente de qual outro cliente?

select conta.numero as conta,cliente_pai ,nome as cliente_dependente
from cliente
join cliente_conta on cliente_conta.id_cliente=cliente.id 
join (select cliente.nome as cliente_pai,cliente_conta.id_conta as conta_pai
      from cliente 
      join cliente_conta on cliente_conta.id_cliente=cliente.id 
      where dependente=false) as clientes_pai
	on conta_pai = cliente_conta.id_conta
join conta on conta.id=cliente_conta.id_conta
where dependente=true
order by conta;

2. Quais foram as 5 contas que:
○ Mais fizeram transações
○ Menos fizeram transações

SELECT
	cliente_conta.id_conta, conta.numero as "numero de conta",
    COUNT(transacao.id) AS "Quantidade_de_trasacao"
FROM transacao
JOIN cliente_conta
	ON transacao.id_cliente_conta = cliente_conta.id
JOIN conta
	ON cliente_conta.id = conta.id
GROUP BY conta.id
ORDER BY Quantidade_de_trasacao DESC
Limit 5;
SELECT
	cliente_conta.id_conta, conta.numero as "numero de conta",
    COUNT(transacao.id) AS "Quantidade_de_trasacao"
FROM transacao
JOIN cliente_conta
	ON transacao.id_cliente_conta = cliente_conta.id
JOIN conta
	ON cliente_conta.id = conta.id
GROUP BY conta.id
ORDER BY Quantidade_de_trasacao asc
Limit 5;

3. Tivemos uma perda de dados e não sabemos qual é o saldo de cada conta, mas temos todas as transações
efetuadas.
○ Queremos saber qual saldo total das contas registradas em banco!
■ Reparem que temos alguns tipos de transações que subtraem dinheiro e outros que
somam.

select conta.numero as conta,depositos.total_depositos, debitos.total_debitos, (depositos.total_depositos-debitos.total_debitos) as saldo
from conta
join (select conta.numero as conta,sum(valor) as total_depositos
	from transacao
	join cliente_conta on cliente_conta.id=transacao.id_cliente_conta
	join conta on conta.id=cliente_conta.id_conta
	where id_tipo_transacao=1
	group by conta) as depositos 
on depositos.conta=conta.numero
join (select conta.numero as conta,sum(valor) as total_debitos
	from transacao
	join cliente_conta on cliente_conta.id=transacao.id_cliente_conta
	join conta on conta.id=cliente_conta.id_conta
	where id_tipo_transacao<>1
	group by conta)as debitos
on debitos.conta=conta.numero;

ou -----------

CREATE VIEW tb_creditos  as select id_cliente_conta as id_temp, SUM(transacao.valor) as creditos
from transacao
where id_tipo_transacao = 1
group by id_cliente_conta;

select id_cliente_conta, tb_creditos.creditos - SUM(transacao.valor)  as saldo_conta
from transacao
inner join tb_creditos on tb_creditos.id_temp = id_cliente_conta
where id_tipo_transacao in (2,3,4)
group by id_cliente_conta
order by saldo_conta asc;




