---
title: Criando atividades personalizados de controle de fluxo
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: de1378cc0dd304db37aefd437d1ce6feac9f2ed2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724644"
---
# <a name="creating-custom-flow-control-activities"></a>Criando atividades personalizados de controle de fluxo
. .NET Framework contém uma variedade de atividades de controle de fluxo que funcionam da mesma forma as estruturas abstratos de programação (como <xref:System.Activities.Statements.Flowchart>) ou as instruções de programação padrão (como <xref:System.Activities.Statements.If>). Este tópico discute a arquitetura de um dos projetos de exemplo, [não genérico ForEach](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Criando a classe personalizada  
 Como a classe não genérico ForEach precisará agendar atividades filhos, precisará derivar de <xref:System.Activities.NativeActivity>, desde que as atividades que derivam de <xref:System.Workflow.Activities.CodeActivity> não têm essa funcionalidade.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 A classe personalizada requer vários membros armazenar os dados que estão sendo usados pela atividade, e fornecer funcionalidade para executar as atividades filhos de atividade. Esses membros incluem:  
  
-   `valueEnumerator`: O não público <xref:System.Activities.Variable%601> do tipo <xref:System.Collections.IEnumerator> usado para iterar sobre a coleção de itens. Esse membro é do tipo <xref:System.Activities.Variable%601> porque ele é usado internamente na atividade, em vez de um argumento ou uma propriedade pública, que são usados se este objeto não ter uma fonte fora da atividade.  
  
-   `OnChildComplete`: O público <xref:System.Activities.CompletionCallback> propriedade que é executado quando cada filho concluir a execução. Esse membro é definido como uma propriedade de CLR, desde que o valor não será alterada para instâncias diferentes de atividade.  
  
-   `Values`: A coleção de entradas usadas para as iterações da atividade filho. Esse membro é do tipo <xref:System.Activities.InArgument%601>, desde que a fonte de dados está fora da atividade, mas o conteúdo da coleção não deverão ser alterado durante a execução da atividade. Se a atividade precisar da funcionalidade de modificar o conteúdo dessa coleção quando a atividade estava executando (para adicionar ou remover atividades, por exemplo), esse membro seria definido como <xref:System.Activities.ActivityAction>, que lhe poderiam ser avaliados em todas as vezes foram acessados, de modo que as alterações eles fiquem disponíveis para a atividade.  
  
-   `Body`: Este membro define a atividade a ser executada para cada item no `Values` coleção. Esse membro é definido como <xref:System.Activities.ActivityAction> de modo que ela é avaliado todas as vezes é acessado.  
  
-   `Execute`: Esse método usa o `InternalExecute`, `OnForEachComplete`, e `GetStateAndExecute` membros não públicos para agendar a execução e atribuir o manipulador de conclusão da atividade filho definida no corpo de membro.  
  
-   `CacheMetadata`: Esse membro fornece o tempo de execução com as informações necessárias para executar a atividade. Por padrão, o método de `CacheMetadata` de uma atividade informará o tempo de execução de todos os membros públicos de atividade, mas como esta atividade usa membros particulares para algumas funcionalidades, precisa informar o tempo de execução de sua existência de modo que o tempo de execução pode estar ciente deless. Nesse caso, a função de `CacheMetadata` é substituída de modo que o membro particular de `valueEnumerator` pode ser acessado. Esse membro também cria um argumento para os valores para atividades de modo que eles possam ser passados à atividade durante a execução.
