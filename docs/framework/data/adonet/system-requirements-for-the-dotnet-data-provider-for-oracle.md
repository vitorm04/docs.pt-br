---
title: Requisitos do sistema para o provedor de dados do .NET Framework para Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: dab3378d3022c01c674640201a67f3bdbb4f571f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174245"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Requisitos do sistema para o provedor de dados do .NET Framework para Oracle

O .NET Framework Data Provider for Oracle requer a versão 2.6 ou posterior do Microsoft Data Access Components (MDAC). Recomenda-se o MDAC 2.8 SP1.  
  
 Você também deve ter o Cliente Oracle 8i Release 3 (8.1.7) ou posteriormente instalado.  
  
 Software Oracle Client antes da versão Oracle 9i não pode acessar bancos de dados UTF16 porque UTF16 é um novo recurso no Oracle 9i. Para usar esse recurso, você deve atualizar seu software cliente para o Oracle 9i ou posterior.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Trabalhando com o Provedor de Dados para Dados Oracle e Unicode  

A seguir está uma lista de problemas relacionados ao Unicode que você deve considerar ao trabalhar com o .NET Framework Data Provider para bibliotecas de clientes Oracle e Oracle. Para obter mais informações, consulte sua documentação Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Definindo o valor unicode em um atributo de seqüência de conexão  

Ao trabalhar com a Oracle, você pode usar o atributo de seqüência de conexões  
  
`Unicode=True`
  
para inicializar as bibliotecas de clientes Oracle no modo UTF-16. Isso faz com que as bibliotecas de clientes Oracle aceitem o UTF-16 (que é muito semelhante ao UCS-2) em vez de strings de vários bytes. Isso permite que o Provedor de Dados da Oracle sempre trabalhe com qualquer página de código Oracle sem trabalho adicional de tradução. Essa configuração só funciona se você estiver usando clientes Oracle 9i para se comunicar com um banco de dados Oracle 9i com o conjunto de caracteres alternativo do AL16UTF16. Quando um cliente Oracle 9i se comunica com um servidor Oracle 9i, são necessários recursos adicionais para converter os valores **do Unicode CommandText** para o conjunto de caracteres de vários bytes apropriado que o servidor Oracle9i usa. Isso pode ser evitado quando você sabe que `Unicode=True` tem a configuração segura adicionando à sua seqüência de conexão.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Misturando versões do Oracle Client e Oracle Server  

Os clientes Oracle 8i não podem acessar dados **NCHAR,** **NVARCHAR2**ou **NCLOB** nos bancos de dados Oracle 9i quando o conjunto nacional de caracteres do servidor é especificado como AL16UTF16 (a configuração padrão do Oracle 9i). Como o suporte para o conjunto de caracteres UTF-16 não foi introduzido até que o Oracle 9i, os clientes Oracle 8i não possam lê-lo.  
  
### <a name="working-with-utf-8-data"></a>Trabalhando com dados UTF-8  

Para definir o conjunto de caracteres alternativos, defina a tecla de registro HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG para UTF8. Consulte as notas de instalação da Oracle em sua plataforma para obter mais informações. A configuração padrão é o conjunto de caracteres principal do idioma a partir do qual você está instalando o software Oracle Client. Não definir o idioma para corresponder ao conjunto de caracteres de idioma nacional do banco de dados ao qual você está se conectando causará vinculações de parâmetros e colunas para enviar ou receber dados em seu conjunto de caracteres de banco de dados principal, não no conjunto nacional de caracteres.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob só pode atualizar caracteres completos.  

Por razões de <xref:System.Data.OracleClient.OracleLob> usabilidade, o objeto herda da classe .NET Framework Stream e fornece métodos **ReadByte** e **WriteByte.** Ele também implementa métodos, como **CopyTo** e **Apagar,** que funcionam em seções de objetos **ORACLE LOB.** Em contraste, o software cliente Oracle fornece uma série de APIs para trabalhar com **lobs**de caracteres **(CLOB** e **NCLOB).** No entanto, essas APIs funcionam apenas em caracteres completos. Devido a essa diferença, o Provedor de Dados para Oracle implementa o suporte para **Leitura** e **ReadByte** para trabalhar com dados UTF-16 de forma byte-wise. No entanto, os outros métodos do objeto **OracleLob** só permitem operações de caractere completo.  
  
## <a name="see-also"></a>Confira também

- [Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)
- [Visão geral do ADO.NET](ado-net-overview.md)
