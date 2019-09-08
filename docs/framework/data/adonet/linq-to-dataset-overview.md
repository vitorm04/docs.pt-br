---
title: LINQ para visão geral do DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: de49febdc81eaf4f487423c5804d1e5cc897cdce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794970"
---
# <a name="linq-to-dataset-overview"></a>LINQ para visão geral do DataSet
O <xref:System.Data.DataSet> é um dos componentes mais amplamente usados do ADO.net. É um elemento-chave do modelo de programação desconectado no qual o ADO.NET se baseia e permite que você armazene explicitamente os dados de diferentes fontes de dados. Para a camada de apresentação, <xref:System.Data.DataSet> o é totalmente integrado com controles de GUI para vinculação de dados. Para a camada intermediária, ele fornece um cache que preserva a forma relacional dos dados e inclui serviços rápidos de navegação de hierarquia e consulta simples. Uma técnica comum usada para reduzir o número de solicitações em um banco de dados é usar <xref:System.Data.DataSet> o para caching na camada intermediária. Por exemplo, considere um aplicativo Web ASP.NET controlado por dados. Geralmente, uma parte significativa de dados do aplicativo não muda com frequência e é comum em sessões ou usuários. Esses dados podem ser mantidos na memória no servidor Web, reduzindo o número de solicitações no banco de dados e acelerando as interações do usuário. Outro aspecto útil do <xref:System.Data.DataSet> é que ele permite que um aplicativo traga subconjuntos de dados de uma ou mais fontes de dados para o espaço do aplicativo. O aplicativo pode manipular os dados na memória, mantendo sua forma relacional.  
  
 Apesar de sua importância, o <xref:System.Data.DataSet> limitou os recursos de consulta. O método <xref:System.Data.DataTable.Select%2A> pode ser usado para filtrar e classificar, e os métodos <xref:System.Data.DataRow.GetChildRows%2A> e <xref:System.Data.DataRow.GetParentRow%2A> podem ser usados para navegação a hierarquia. Para algo mais complexo, no entanto, o desenvolvedor precisa escrever uma consulta personalizada. Isso pode resultar em aplicativos com baixo desempenho e de difícil manutenção.  
  
 LINQ to DataSet torna mais fácil e rápido a consulta sobre dados armazenados em cache em <xref:System.Data.DataSet> um objeto. Essas consultas são expressas na própria linguagem de programação, e não como os literais de cadeia de caracteres inseridos no código do aplicativo. Isso significa que os desenvolvedores não precisam aprender uma linguagem de consulta separada. Além disso, LINQ to DataSet permite que os desenvolvedores do Visual Studio trabalhem de forma mais produtiva, porque o IDE do Visual Studio fornece verificação de sintaxe de tempo de compilação [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], digitação estática e suporte do IntelliSense para o. LINQ to DataSet também pode ser usado para consultar dados que foram consolidados de uma ou mais fontes de dados. Isso habilita vários cenários que exigem flexibilidade na maneira como dados são representados e tratados. Em particular, relatórios genéricos, análises e business intelligence aplicativos exigem esse método de manipulação.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Consultando DataSets usando o LINQ to DataSet  
 Antes de começar a consultar um <xref:System.Data.DataSet> objeto usando LINQ to DataSet, você deve preencher o. <xref:System.Data.DataSet> Há várias maneiras de carregar dados em um <xref:System.Data.DataSet>, como usar a <xref:System.Data.Common.DataAdapter> classe ou [LINQ to SQL](./sql/linq/index.md). Depois que os dados tiverem sido carregados em <xref:System.Data.DataSet> um objeto, você poderá começar a consultá-los. As consultas do formular usando LINQ to DataSet é semelhante [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] ao uso [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]de outras fontes de dados habilitadas. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]as consultas podem ser executadas em tabelas únicas em <xref:System.Data.DataSet> uma ou em mais de uma tabela usando os <xref:System.Linq.Enumerable.Join%2A> operadores <xref:System.Linq.Enumerable.GroupJoin%2A> de consulta e padrão.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]Há suporte para consultas em <xref:System.Data.DataSet> objetos digitados e não tipados. Se o esquema do <xref:System.Data.DataSet> for conhecido no momento do design do aplicativo, um tipo <xref:System.Data.DataSet> será recomendado. Em um tipo <xref:System.Data.DataSet>, as tabelas e linhas têm Membros digitados para cada uma das colunas, o que torna as consultas mais simples e legíveis.  
  
 Além dos operadores de consulta padrão implementados em System. Core. dll, LINQ to DataSet adiciona várias <xref:System.Data.DataSet>extensões específicas que facilitam a consulta em um conjunto de <xref:System.Data.DataRow> objetos. Essas extensões específicas de <xref:System.Data.DataSet> incluem operadores para comparar sequências de linhas, bem como métodos que fornecem acesso aos valores de coluna de <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Aplicativos de n camadas e LINQ to DataSet  
 Aplicativos de dados de n camadas são aplicativos centrados em dados que são separados em várias camadas lógicas (ou camadas). Um aplicativo de n camadas típico inclui uma camada de apresentação, uma camada intermediária e uma camada de dados. Dividir componentes do aplicativo em camadas separadas aumenta a facilidade de manutenção e a escalabilidade do aplicativo. Para obter mais informações sobre aplicativos de dados de N camadas, consulte [trabalhar com conjuntos de dados em aplicativos de n camadas](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 Em aplicativos de n camadas, o <xref:System.Data.DataSet> costuma ser usado na camada intermediária para armazenar em cache informações para um aplicativo Web. A funcionalidade de consulta de LINQ to DataSet é implementada por meio de métodos de extensão e <xref:System.Data.DataSet>estende o ADO.NET 2,0 existente.  
  
## <a name="see-also"></a>Consulte também

- [Consultando DataSets](querying-datasets-linq-to-dataset.md)
- [LINQ (consulta integrada à linguagem) – C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (consulta integrada à linguagem) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
