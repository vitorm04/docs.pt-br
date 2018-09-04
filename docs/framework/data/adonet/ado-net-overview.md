---
title: Visão geral do ADO.NET
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 697911201171a540d6749d03c51f14efba945765
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489806"
---
# <a name="adonet-overview"></a>Visão geral do ADO.NET
O ADO.NET fornece acesso consistente a fontes de dados como o SQL Server e o XML, e a fontes de dados expostas através do OLE DB e do ODBC. Os aplicativos do consumidor de compartilhamento de dados podem usar o ADO.NET para se conectar a essas fontes de dados, e para recuperar, manipular e atualizar os dados nelas contidos.  
  
 O ADO.NET separa o acesso a dados da manipulação de dados em componentes discretos que podem ser usados separadamente ou em tandem. O ADO.NET inclui os provedores de dados do .NET Framework para se conectar a um banco de dados, executar comandos e recuperar resultados. Esses resultados são processados diretamente, colocados em um objeto <xref:System.Data.DataSet> do ADO.NET para serem expostos para o usuário ad hoc, combinados com dados de várias fontes ou passados entre as camadas. O objeto `DataSet` também pode ser usado independentemente de um provedor de dados .NET Framework para gerenciar o local dos dados para o aplicativo ou originado no XML.  
  
 As classes do ADO.NET estão no System.Data.dll e são integradas às classes XML encontradas no System.Xml.dll. Para código de exemplo que se conecta a um banco de dados, recupera dados dele e, em seguida, exibe os dados em uma janela do console, consulte [exemplos de código ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 O ADO.NET fornece a funcionalidade para os desenvolvedores que gravam um código gerenciado semelhante à funcionalidade fornecida aos desenvolvedores COM nativos pelos objetos ActiveX Data Objects (ADO). É recomendável que você use o ADO.NET, e não o ADO, para acessar dados nos aplicativos .NET.  
  
 O ADO.NET fornece o método mais direto de acesso a dados no .NET Framework. Para uma abstração de nível superior que permite que os aplicativos funcionam em um modelo conceitual em vez do modelo de armazenamento subjacente, consulte o [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Declaração de privacidade**: assemblies a dll, privacidade&lt;1, OracleClient, dll, System, SqlServerCe. dll e DataSetExtensions. dll não distingui entre um usuário dados particulares e não privados.  Esses assemblies não coletam, não armazenam nem transmitem dados privados de nenhum usuário. No entanto, os aplicativos de terceiros podem coletar, armazenar ou transmitir dados privados de um usuário usando esses assemblies.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Arquitetura do ADO.NET](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Fornece uma visão geral da arquitetura e dos componentes do ADO.NET.  
  
 [Opções e diretrizes da tecnologia ADO.NET](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Descreve os produtos e as tecnologias incluídos na plataforma de dados de entidade.  
  
 [LINQ e ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Descreve como a consulta integrada à linguagem (LINQ) é implementada no ADO.NET e fornece links para tópicos relevantes.  
  
 [Provedores de dados do .NET Framework](../../../../docs/framework/data/adonet/data-providers.md)  
 Fornece uma visão geral do design do provedor de dados .NET Framework e dos provedores de dados .NET Framework incluídos no ADO.NET.  
  
 [DataSets ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Fornece uma visão geral do design e dos componentes do `DataSet`.  
  
 [Execução lado a lado no ADO.NET](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 Aborda as diferenças entre as versões do ADO.NET e seu efeito na execução lado a lado e na compatibilidade entre aplicativos.  
  
 [Exemplos de código do ADO.NET](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 Fornece exemplos de código que recuperam dados usando os provedores de dados ADO.NET.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [What's New in ADO.NET](../../../../docs/framework/data/adonet/whats-new.md) (Novidades no ADO.NET)  
 Apresenta recursos que são novos no [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 Descreve práticas seguras de codificação ao usar o ADO.NET.  
  
 [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)  
 Descreve os mapeamentos de tipo de dados entre os tipos de dados do .NET Framework e os provedores de dados .NET Framework.  
  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 Descreve como conectar-se a uma fonte de dados, recuperar dados e modificar dados. Isso inclui `DataReaders` e `DataAdapters`.  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Acessando dados no Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
