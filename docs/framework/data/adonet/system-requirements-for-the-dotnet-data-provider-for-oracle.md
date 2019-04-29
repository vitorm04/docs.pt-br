---
title: Requisitos do sistema para o provedor de dados do .NET Framework para Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: 61f8509cce248f6cc0a56900227f9758eb27c4e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698402"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Requisitos do sistema para o provedor de dados do .NET Framework para Oracle
O .NET Framework Data Provider for Oracle requer o Microsoft Data Access Components (MDAC) versão 2.6 ou posterior. MDAC 2.8 SP1 é recomendado.  
  
 Você também deve ter o cliente do Oracle 8i versão 3 (8.1.7) ou posterior instalado.  
  
 Software de cliente Oracle antes da versão Oracle 9i não pode acessar bancos de dados UTF16 porque UTF16 é um novo recurso no Oracle 9i. Para usar esse recurso, você deve atualizar o software cliente Oracle 9i ou posterior.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Trabalhando com o provedor de dados para Oracle e dados Unicode  
 A seguir está uma lista dos problemas relacionados a Unicode que você deve considerar ao trabalhar com o provedor de dados do .NET Framework para Oracle e Oracle bibliotecas de cliente. Para obter mais informações, consulte a documentação do Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Definindo o valor de Unicode em um atributo de cadeia de caracteres de Conexão  
 Ao trabalhar com a Oracle, você pode usar o atributo de cadeia de caracteres de conexão  
  
```  
Unicode=True   
```  
  
 para inicializar as bibliotecas de cliente Oracle no modo de UTF-16. Isso faz com que o cliente Oracle bibliotecas aceitar o UTF-16 (que é muito semelhante ao UCS-2), em vez de cadeias de caracteres multibyte. Isso permite que o provedor de dados para Oracle sempre trabalhar com qualquer página de código do Oracle sem trabalho adicional de tradução. Essa configuração só funciona se você estiver usando clientes do Oracle 9i para se comunicar com um banco de dados Oracle 9i com o conjunto de caracteres alternativos de AL16UTF16. Quando um cliente do Oracle 9i se comunica com um servidor do Oracle 9i, são necessários recursos adicionais para converter o Unicode **CommandText** valores para o caractere de multibyte apropriado que defina o Oracle9i server usa. Isso pode ser evitado quando você souber que tem a configuração de segurança, adicionando `Unicode=True` à cadeia de conexão.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Combinação de versões de cliente Oracle e o servidor Oracle  
 Não é possível acessar a clientes do Oracle 8i **NCHAR**, **NVARCHAR2**, ou **NCLOB** dados Oracle 9i bancos de dados quando o conjunto de caracteres nacionais do servidor é especificado como AL16UTF16 (o configuração padrão para o Oracle 9i). Porque o suporte para o conjunto de caracteres UTF-16 não foi introduzido até Oracle 9i, Oracle 8i clientes não podem lê-lo.  
  
### <a name="working-with-utf-8-data"></a>Trabalhando com dados UTF-8  
 Para definir o conjunto de caracteres alternativos, defina o HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG de chave do registro para UTF8. Consulte as notas de instalação do Oracle em sua plataforma para obter mais informações. A configuração padrão é o conjunto de caracteres principal da linguagem na qual você está instalando o software cliente Oracle. Não definindo o idioma para coincidir com o conjunto de caracteres de idioma nacional do banco de dados ao qual você está se conectando fará com que as associações de parâmetro e coluna enviar ou receber dados em seu conjunto de caracteres do banco de dados primário, não o conjunto de caracteres nacionais.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob pode atualizar apenas caracteres completos.  
 Por motivos de usabilidade, os <xref:System.Data.OracleClient.OracleLob> objeto herda a classe Stream do .NET Framework e fornece **ReadByte** e **WriteByte** métodos. Ele também implementa métodos, tais como **CopyTo** e **apagar**, que funcionam em seções do Oracle **LOB** objetos. Em contraste, o software cliente Oracle fornece uma série de APIs para trabalhar com o caractere **LOB**s (**CLOB** e **NCLOB**). No entanto, essas APIs trabalham em apenas caracteres completos. Por causa dessa diferença, o provedor de dados para Oracle implementa o suporte para **leitura** e **ReadByte** para trabalhar com dados UTF-16 de maneira byte-wise. No entanto, os outros métodos do **OracleLob** objeto permitir apenas operações de caractere completo.  
  
## <a name="see-also"></a>Consulte também

- [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
