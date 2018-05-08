---
title: Substituído em Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 899d21f23c0500a1df01916d1da210b2f9bea95b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Substituído em Windows Workflow Foundation
Em .NET 4 a equipe de fluxo de trabalho liberou qualquer novo mecanismo de fluxo de trabalho no espaço de <xref:System.Activities> . Com o lançamento da versão Beta do .NET 4.5, marcar a maioria dos tipos de "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, e <xref:System.Workflow.Runtime> namespaces como obsoleto.  
  
## <a name="obsolete-namespaces-and-tools"></a>Namespaces e ferramentas obsoletas  
 Os seguintes conjuntos possuem um ou mais tipos públicos que serão substituídos:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 Como resultado, os clientes que são substituídos usando APIs de WF 3 encontrarão avisos de compilação com uma mensagem semelhante ao seguinte:  
  
 **Aviso BC40000: X é obsoleta: WF 3 tipos são preteridos. Use o WF 4.** Nós removeremos os tipos do.NET Framework em uma versão futura, mas nós não determinamos ainda esse o prazo (não em 4,5). Esta etapa atual permite que nós comuniquem a direção a nossos clientes e permitam-lhes a abundância hora de mover para o novo modelo WF4. Obviamente, continuaremos a dar suporte a esses tipos de WF 3 no [política de ciclo de vida do suporte da Microsoft](http://aka.ms/MicrosoftSupportLifecycle). Os aplicativos WF3 existentes serão executados sem problema no .NET 4.5, e [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ele novos e existentes de soluções WF3-based.  
  
 As regras tipos relacionados ao espaço de <xref:System.Workflow.Activities.Rules> , que não têm uma substituição em WF 4,5, não foram substituídas dentro.  
  
 Os clientes que desejam migrar seus aplicativos para o WF 4 encontrará ajuda a [orientação de migração do fluxo de trabalho 4](migration-guidance.md).
