---
title: Personalizando a experiência design de fluxo de trabalho
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141931"
---
# <a name="customizing-the-workflow-design-experience"></a>Personalizando a experiência design de fluxo de trabalho

Os cenários para a criação de atividades personalizadas e a rehospedagem dos [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] foram bastante simplificados no .NET Framework 4. O desenvolvimento e implantação agora são mais fácil e mais flexível. A chave infraestrutura alterada é que o novo modelo de programação do designer de atividade é criado sobre Windows Presentation Foundation (WPF). Isso fornece a capacidade de definir designer de atividade declarativamente e o rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] em outros aplicativos com fácil comparativo. Ao rehosting, um editor de expressão personalizado pode ser desenvolvido para oferecer suporte IntelliSense ou um domínio simplificado da expressão. A integração com o Windows Communication Foundation (WCF) se tornou mais direta com o uso dos serviços de fluxo de trabalho. Designers personalizados de atividade e a árvore modelo de item podem ser usados para aprimorar experiências de tempo de design em designer rehosted de fluxo de trabalho.

## <a name="in-this-section"></a>Nesta seção

 [Usando designers e modelos de atividade personalizados](using-custom-activity-designers-and-templates.md)

 Descreve como criar novos designer personalizadas e modelos de atividade.

 [Hospedando novamente o Designer de Fluxo de Trabalho](rehosting-the-workflow-designer.md)

 Descreve como hospedar novamente o [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] fora do Visual Studio e como exibir erros de validação.

 [Usando um editor de expressão personalizado](using-a-custom-expression-editor.md)

 Descreve como implementar um editor de expressão personalizado para usar com designers de fluxo de trabalho rehospedados fora do Visual Studio 2010.

## <a name="reference"></a>Referência

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>Consulte também

- [Estendendo o Windows Workflow Foundation](extend.md)
- [Designer](./samples/designer.md)
- [Designers de atividade personalizada](./samples/custom-activity-designers.md)
- [Mudança de host de designer](./samples/designer-rehosting.md)
