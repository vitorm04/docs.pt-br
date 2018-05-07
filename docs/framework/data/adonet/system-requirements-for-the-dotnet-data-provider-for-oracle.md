---
title: Requisitos do sistema para o provedor de dados do .NET Framework para Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: a5ce0e831af40cbe86e6ac901d6e92d5a60f8774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Requisitos do sistema para o provedor de dados do .NET Framework para Oracle
O provedor de dados .NET Framework para Oracle requer Microsoft Data Access Components (MDAC) versão 2.6 ou posterior. MDAC 2.8 SP1 é recomendado.  
  
 Você também deve ter o cliente do Oracle 8i versão 3 (8.1.7) ou posterior instalado.  
  
 Cliente Oracle anteriores à versão 9i Oracle não pode acessar bancos de dados UTF16 porque UTF16 é um novo recurso no Oracle 9i. Para usar esse recurso, você deve atualizar o software cliente Oracle 9i ou posterior.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Trabalhando com o provedor de dados do Oracle e dados Unicode  
 A seguir está uma lista de problemas relacionados a Unicode que você deve considerar ao trabalhar com o provedor de dados .NET Framework para Oracle e Oracle bibliotecas de cliente. Para obter mais informações, consulte a documentação do Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Definir o valor de Unicode em um atributo de cadeia de caracteres de Conexão  
 Ao trabalhar com o Oracle, você pode usar o atributo de cadeia de caracteres de conexão  
  
```  
Unicode=True   
```  
  
 para inicializar as bibliotecas de cliente Oracle no modo de UTF-16. Isso faz com que o cliente Oracle bibliotecas aceitar UTF-16 (que é muito semelhante ao UCS-2) em vez de cadeias de caracteres multibyte. Isso permite que o provedor de dados Oracle trabalhar sempre com qualquer página de código do Oracle sem trabalho adicional de tradução. Essa configuração só funciona se você estiver usando os clientes do Oracle 9i para se comunicar com um banco de dados Oracle 9i com o conjunto de caracteres alternativos de AL16UTF16. Quando um cliente do Oracle 9i se comunica com um servidor do Oracle 9i, recursos adicionais são necessárias para converter o Unicode **CommandText** valores para o caracteres multibyte apropriado que definir o Oracle9i usa o servidor. Isso pode ser evitado quando você souber que tem a configuração de segurança adicionando `Unicode=True` em sua cadeia de caracteres de conexão.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Mistura de versões de cliente Oracle e o servidor Oracle  
 Não é possível acessar os clientes do Oracle 8i **NCHAR**, **NVARCHAR2**, ou **NCLOB** dados no Oracle 9i bancos de dados quando o conjunto de caracteres nacionais do servidor é especificado como AL16UTF16 (o configuração padrão para o Oracle 9i). Porque o suporte para o conjunto de caracteres UTF-16 não foi introduzido até Oracle 9i, Oracle 8i clientes não podem lê-lo.  
  
### <a name="working-with-utf-8-data"></a>Trabalhando com dados UTF-8  
 Para definir o conjunto de caracteres alternativo, defina o HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG de chave do registro para UTF8. Consulte as notas de instalação do Oracle em sua plataforma para obter mais informações. A configuração padrão é o conjunto de caracteres principal do idioma do qual você está instalando o software cliente Oracle. Não definir o idioma para coincidir com o conjunto de caracteres do idioma nacional do banco de dados ao qual você está se conectando fará com que as associações de coluna e parâmetro enviar ou receber dados no seu conjunto de caracteres de banco de dados primário, não o conjunto de caracteres nacionais.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob pode atualizar somente os caracteres completas.  
 Por motivos de usabilidade, o <xref:System.Data.OracleClient.OracleLob> objeto herda da classe de fluxo do .NET Framework e fornece **ReadByte** e **WriteByte** métodos. Ele também implementa métodos, como **CopyTo** e **apagar**, que funcionam em seções do Oracle **LOB** objetos. Em contraste, o software cliente Oracle fornece várias APIs para trabalhar com o caractere **LOB**s (**CLOB** e **NCLOB**). No entanto, essas APIs funcionam apenas caracteres completa. Devido a essa diferença, o provedor de dados Oracle implementa o suporte para **leitura** e **ReadByte** para trabalhar com dados UTF-16 de maneira byte-wise. No entanto, os outros métodos do **OracleLob** objeto apenas permitir operações de caractere completo.  
  
## <a name="see-also"></a>Consulte também  
 [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
