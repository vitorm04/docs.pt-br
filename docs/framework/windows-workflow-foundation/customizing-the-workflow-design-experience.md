---
title: Personalizando a experiência design de fluxo de trabalho
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 926edb4478551affa03619f44ee886d5eb591e4d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637248"
---
# <a name="customizing-the-workflow-design-experience"></a>Personalizando a experiência design de fluxo de trabalho

Cenários para criar atividades personalizados e para rehosting [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] simplificados foram bastante em [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. O desenvolvimento e implantação agora são mais fácil e mais flexível. A alteração infraestrutural chave é que o novo modelo de programação de atividade designer baseia-se ao Windows Presentation Foundation (WPF). Isso fornece a capacidade de definir designer de atividade declarativamente e o rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] em outros aplicativos com fácil comparativo. Ao rehosting, um editor de expressão personalizado pode ser desenvolvido para oferecer suporte IntelliSense ou um domínio simplificado da expressão. A integração com o Windows Communication Foundation (WCF) tornou-se mais integrada com o uso dos serviços de fluxo de trabalho. Designers personalizados de atividade e a árvore modelo de item podem ser usados para aprimorar experiências de tempo de design em designer rehosted de fluxo de trabalho.

## <a name="in-this-section"></a>Nesta seção

 [Usando designers e modelos de atividade personalizados](using-custom-activity-designers-and-templates.md)

 Descreve como criar novos designer personalizadas e modelos de atividade.

 [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)

 Descreve como hospedar novamente o [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] fora do Visual Studio e como exibir erros de validação.

 [Usando um editor de expressão personalizado](using-a-custom-expression-editor.md)

 Descreve como implementar um editor de expressão personalizada para usar com designers de fluxo de trabalho rehosted fora do Visual Studio 2010.

## <a name="reference"></a>Referência

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Consulte também

- [Estendendo o Windows Workflow Foundation](extend.md)
- [Designer](./samples/designer.md)
- [Designers de atividade personalizada](./samples/custom-activity-designers.md)
- [Mudança de host de designer](./samples/designer-rehosting.md)
