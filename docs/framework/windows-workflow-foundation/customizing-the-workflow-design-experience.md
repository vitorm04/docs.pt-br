---
title: Personalizando a experiência design de fluxo de trabalho
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 27be398d874747b65ae051224070d3f40f1fbbb0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715132"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="8b7f3-102">Personalizando a experiência design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8b7f3-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="8b7f3-103">Os cenários para criar atividades personalizadas e rehospedar as Designer de Fluxo de Trabalho do Windows foram bastante simplificados no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-103">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="8b7f3-104">O desenvolvimento e implantação agora são mais fácil e mais flexível.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="8b7f3-105">A chave infraestrutura alterada é que o novo modelo de programação do designer de atividade é criado sobre Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="8b7f3-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="8b7f3-106">Isso permite que você defina os designers de atividade declarativamente e rehospede o Designer de Fluxo de Trabalho em outros aplicativos com o comparativa fácil.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-106">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="8b7f3-107">Ao rehosting, um editor de expressão personalizado pode ser desenvolvido para oferecer suporte IntelliSense ou um domínio simplificado da expressão.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="8b7f3-108">A integração com o Windows Communication Foundation (WCF) se tornou mais direta com o uso dos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="8b7f3-109">Designers personalizados de atividade e a árvore modelo de item podem ser usados para aprimorar experiências de tempo de design em designer rehosted de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8b7f3-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8b7f3-110">In This Section</span></span>

 [<span data-ttu-id="8b7f3-111">Usando designers e modelos de atividade personalizados</span><span class="sxs-lookup"><span data-stu-id="8b7f3-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="8b7f3-112">Descreve como criar novos designer personalizadas e modelos de atividade.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="8b7f3-113">Hospedando novamente o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="8b7f3-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="8b7f3-114">Descreve como hospedar novamente o Designer de Fluxo de Trabalho do Windows fora do Visual Studio e como exibir erros de validação.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-114">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="8b7f3-115">Usando um editor de expressão personalizado</span><span class="sxs-lookup"><span data-stu-id="8b7f3-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="8b7f3-116">Descreve como implementar um editor de expressão personalizado para usar com designers de fluxo de trabalho rehospedados fora do Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="8b7f3-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="8b7f3-117">Referência</span><span class="sxs-lookup"><span data-stu-id="8b7f3-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="8b7f3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b7f3-118">See also</span></span>

- [<span data-ttu-id="8b7f3-119">Estendendo o Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="8b7f3-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="8b7f3-120">Designer</span><span class="sxs-lookup"><span data-stu-id="8b7f3-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="8b7f3-121">Designers de atividade personalizada</span><span class="sxs-lookup"><span data-stu-id="8b7f3-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="8b7f3-122">Mudança de host de designer</span><span class="sxs-lookup"><span data-stu-id="8b7f3-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
