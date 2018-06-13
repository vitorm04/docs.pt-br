---
title: Atividades em tempo de execução de WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513029"
---
# <a name="runtime-activities-in-wf"></a>Atividades em tempo de execução de WF
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] fornece vários sistema forneceu atividades acessando recursos de tempo de execução de fluxo de trabalho, como a persistência e o encerramento.  
  
|Atividade|Descrição|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|Solicita explicitamente que o fluxo de trabalho persiste seu estado.|  
|<xref:System.Activities.Statements.TerminateWorkflow>|Finaliza a instância em execução de fluxo de trabalho.|  
|<xref:System.Activities.Statements.NoPersistScope>|Uma atividade do contêiner que impede que as atividades filhos persistam.|
