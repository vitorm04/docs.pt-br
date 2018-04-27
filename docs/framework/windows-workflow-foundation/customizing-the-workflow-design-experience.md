---
title: Personalizando a experiência design de fluxo de trabalho
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ee64ae3db9dbf98f2a62397075406c118a867bb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-the-workflow-design-experience"></a>Personalizando a experiência design de fluxo de trabalho
Cenários para criar atividades personalizados e para rehosting [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] simplificados foram bastante em [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. O desenvolvimento e implantação agora são mais fácil e mais flexível. A alteração da chave de base é que o novo modelo de programação de atividade designer foi criado no Windows Presentation Foundation (WPF). Isso fornece a capacidade de definir designer de atividade declarativamente e o rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] em outros aplicativos com fácil comparativo. Ao rehosting, um editor de expressão personalizado pode ser desenvolvido para oferecer suporte IntelliSense ou um domínio simplificado da expressão. Integração com [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] tornou-se mais integrada com uso de serviços de fluxo de trabalho. Designers personalizados de atividade e a árvore modelo de item podem ser usados para aprimorar experiências de tempo de design em designer rehosted de fluxo de trabalho.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Usando designers e modelos de atividade personalizados](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 Descreve como criar novos designer personalizadas e modelos de atividade.  
  
 [Hospedando novamente o Designer de Fluxo de Trabalho](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 Descreve como novamente o host [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] fora de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] e como exibir erros de validação.  
  
 [Usando um editor de expressão personalizado](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 Descreve como implementar uma editor de expressão personalizado para usar com designers de fluxo de trabalho rehosted fora de [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
## <a name="reference"></a>Referência  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [Designer](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [Designers de atividade personalizada](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [Mudança de host de designer](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
