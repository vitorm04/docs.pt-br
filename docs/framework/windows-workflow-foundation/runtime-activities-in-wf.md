---
title: "Atividades em tempo de execução de WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3aca3fcdd4fa8d73bf3412d7c20697847d0a699
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-activities-in-wf"></a>Atividades em tempo de execução de WF
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] fornece vários sistema forneceu atividades acessando recursos de tempo de execução de fluxo de trabalho, como a persistência e o encerramento.  
  
|Atividade|Descrição|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|Solicita explicitamente que o fluxo de trabalho persiste seu estado.|  
|<xref:System.Activities.Statements.TerminateWorkflow>|Finaliza a instância em execução de fluxo de trabalho.|  
|<xref:System.Activities.Statements.NoPersistScope>|Uma atividade do contêiner que impede que as atividades filhos persistam.|
