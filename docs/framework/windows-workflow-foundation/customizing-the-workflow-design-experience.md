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
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="8292c-102">Personalizando a experiência design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8292c-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="8292c-103">Cenários para criar atividades personalizados e para rehosting [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] simplificados foram bastante em [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8292c-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="8292c-104">O desenvolvimento e implantação agora são mais fácil e mais flexível.</span><span class="sxs-lookup"><span data-stu-id="8292c-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="8292c-105">A alteração infraestrutural chave é que o novo modelo de programação de atividade designer baseia-se ao Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="8292c-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="8292c-106">Isso fornece a capacidade de definir designer de atividade declarativamente e o rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] em outros aplicativos com fácil comparativo.</span><span class="sxs-lookup"><span data-stu-id="8292c-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="8292c-107">Ao rehosting, um editor de expressão personalizado pode ser desenvolvido para oferecer suporte IntelliSense ou um domínio simplificado da expressão.</span><span class="sxs-lookup"><span data-stu-id="8292c-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="8292c-108">A integração com o Windows Communication Foundation (WCF) tornou-se mais integrada com o uso dos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8292c-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="8292c-109">Designers personalizados de atividade e a árvore modelo de item podem ser usados para aprimorar experiências de tempo de design em designer rehosted de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8292c-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8292c-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8292c-110">In This Section</span></span>

 [<span data-ttu-id="8292c-111">Usando designers e modelos de atividade personalizados</span><span class="sxs-lookup"><span data-stu-id="8292c-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="8292c-112">Descreve como criar novos designer personalizadas e modelos de atividade.</span><span class="sxs-lookup"><span data-stu-id="8292c-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="8292c-113">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="8292c-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="8292c-114">Descreve como hospedar novamente o [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] fora do Visual Studio e como exibir erros de validação.</span><span class="sxs-lookup"><span data-stu-id="8292c-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="8292c-115">Usando um editor de expressão personalizado</span><span class="sxs-lookup"><span data-stu-id="8292c-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="8292c-116">Descreve como implementar um editor de expressão personalizada para usar com designers de fluxo de trabalho rehosted fora do Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8292c-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="8292c-117">Referência</span><span class="sxs-lookup"><span data-stu-id="8292c-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="8292c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8292c-118">See also</span></span>

- [<span data-ttu-id="8292c-119">Estendendo o Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="8292c-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="8292c-120">Designer</span><span class="sxs-lookup"><span data-stu-id="8292c-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="8292c-121">Designers de atividade personalizada</span><span class="sxs-lookup"><span data-stu-id="8292c-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="8292c-122">Mudança de host de designer</span><span class="sxs-lookup"><span data-stu-id="8292c-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
