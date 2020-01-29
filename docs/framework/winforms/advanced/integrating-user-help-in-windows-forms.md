---
title: Integrando a ajuda do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: c402615d68c75327613d21bd35f1587b10f1dbf3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731571"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="ead3c-102">Integrando a ajuda do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ead3c-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="ead3c-103">Um aspecto essencial, mas geralmente esquecido, da criação de aplicativos baseados no Windows é o sistema de Ajuda, pois é onde os usuários obtêm assistência em tempos de confusão.</span><span class="sxs-lookup"><span data-stu-id="ead3c-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="ead3c-104">O Windows Forms oferece suporte a dois tipos diferentes de Ajuda, cada um fornecido pelo [Componente HelpProvider](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ead3c-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="ead3c-105">O primeiro envolve apontar o usuário para um arquivo de ajuda de HTML ou HTML Help 1.*x* ou um formato maior.</span><span class="sxs-lookup"><span data-stu-id="ead3c-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="ead3c-106">O segundo pode exibir a Ajuda breve "O que é isto" em controles individuais; Isso é especialmente útil em caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ead3c-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="ead3c-107">Ambos os tipos da Ajuda podem ser usados no mesmo formulário.</span><span class="sxs-lookup"><span data-stu-id="ead3c-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="ead3c-108">Além disso, o [Componente ToolTip](../controls/tooltip-component-windows-forms.md) pode ser usado para fornecer Ajuda individual para controles nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ead3c-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ead3c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ead3c-109">In This Section</span></span>  
 [<span data-ttu-id="ead3c-110">Como Fornecer Ajuda em um Aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="ead3c-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="ead3c-111">Explica como usar o componente `HelpProvider` para vincular controles a arquivos em um sistema de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="ead3c-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="ead3c-112">Como Exibir Ajuda Pop-up</span><span class="sxs-lookup"><span data-stu-id="ead3c-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="ead3c-113">Explica como usar o componente `HelpProvider` para exibir a Ajuda pop-up nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ead3c-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="ead3c-114">Ajuda de Controle Usando ToolTips</span><span class="sxs-lookup"><span data-stu-id="ead3c-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="ead3c-115">Descreve como usar o componente `ToolTip` para exibir a Ajuda específica do Ajuda.</span><span class="sxs-lookup"><span data-stu-id="ead3c-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ead3c-116">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="ead3c-116">Related Sections</span></span>  
 [<span data-ttu-id="ead3c-117">Componente HelpProvider</span><span class="sxs-lookup"><span data-stu-id="ead3c-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="ead3c-118">Explica os conceitos básicos do componente `HelpProvider`.</span><span class="sxs-lookup"><span data-stu-id="ead3c-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="ead3c-119">Componente ToolTip</span><span class="sxs-lookup"><span data-stu-id="ead3c-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="ead3c-120">Explica os conceitos básicos do componente `ToolTip`.</span><span class="sxs-lookup"><span data-stu-id="ead3c-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="ead3c-121">Visão geral dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ead3c-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="ead3c-122">Explica os conceitos básicos dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ead3c-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="ead3c-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ead3c-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="ead3c-124">Fornece uma visão geral dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ead3c-124">Provides an overview of Windows Forms.</span></span>
