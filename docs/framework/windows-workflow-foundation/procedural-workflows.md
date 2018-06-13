---
title: Fluxos de trabalho procedurais
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 5cd97c8ccaae74e4275f809502ac0a4d3c2f042a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515223"
---
# <a name="procedural-workflows"></a>Fluxos de trabalho procedurais
Fluxos de trabalho procedurais usam métodos de controle de fluxo semelhantes a esses elementos encontrados em idiomas procedurais. Essas construções incluem `While` e `If`. Esses fluxos de trabalho podem ser compostos livremente usando outras atividades de controle de fluxo como <xref:System.Activities.Statements.Flowchart> e <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Fluxo de controle de execução  
 A biblioteca de atividade de fluxo de trabalho tem atividades para modelar a maioria dos métodos de controle de fluxo usados em idiomas procedurais. Elas incluem:  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Para usar atividades de fluxo de controle, arraste e solte-os do **atividade** caixa de ferramentas em uma atividade composta dentro da janela do designer.  
  
> [!NOTE]
>  Se usando [!INCLUDE[dublin](../../../includes/dublin-md.md)] para hospedar fluxos de trabalho em uma Web farm, AppFabric moverá instâncias entre servidores diferentes de AppFabric. Isso requer que os recursos podem ser compartilhado entre todos os nós.  Nenhuma das atividades padrão de fluxo de trabalho de REDE 4 contêm todas as operações que acessam recursos locais. Desde que AppFabric não oferece nenhum mecanismo marcar um fluxo de trabalho ainda, como um desenvolvedor não deve criar as atividades personalizados que elas falham quando um fluxo de trabalho é movido.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxos de trabalho de fluxograma](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
