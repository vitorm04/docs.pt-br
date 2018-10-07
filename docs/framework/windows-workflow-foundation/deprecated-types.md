---
title: Substituído em Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: d41bf147cd079a3d6d3714da5595732de3dcb7de
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847432"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Substituído em Windows Workflow Foundation
Em .NET 4 a equipe de fluxo de trabalho liberou qualquer novo mecanismo de fluxo de trabalho no espaço de <xref:System.Activities> . Com o lançamento do .NET Beta 4.5 nós estamos marcando a maioria dos tipos em "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, e <xref:System.Workflow.Runtime> namespaces como obsoleto.  
  
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
  
 **BC40000 de aviso: X é obsoleto: tipos de WF 3 são substituídos. Use o WF 4.** Nós removeremos os tipos do.NET Framework em uma versão futura, mas nós não determinamos ainda esse o prazo (não em 4,5). Esta etapa atual permite que nós comuniquem a direção a nossos clientes e permitam-lhes a abundância hora de mover para o novo modelo WF4. Claro, continuaremos a dar suporte a esses tipos de WF 3 sob o [política de ciclo de vida do suporte da Microsoft](https://aka.ms/MicrosoftSupportLifecycle). Os aplicativos WF3 existentes serão executados sem problema no .NET 4.5 e Visual Studio 2012 oferecerá suporte a soluções WF3-based novas e existentes.  
  
 As regras tipos relacionados ao espaço de <xref:System.Workflow.Activities.Rules> , que não têm uma substituição em WF 4,5, não foram substituídas dentro.  
  
 Os clientes que desejam migrar seus aplicativos para o WF 4 localizarão a Ajuda do [diretrizes de migração do fluxo de trabalho 4](migration-guidance.md).
