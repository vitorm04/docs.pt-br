---
title: "Criação de atividade de fluxo de trabalho usando a classe de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4fc6d0807c07952e9b3abe2861ef04bc225142f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="6c14d-102">Criação de atividade de fluxo de trabalho usando a classe de atividades</span><span class="sxs-lookup"><span data-stu-id="6c14d-102">Workflow Activity Authoring Using the Activity Class</span></span>
<span data-ttu-id="6c14d-103">A maneira mais simples para criar uma atividade usando [!INCLUDE[wf](../../../includes/wf-md.md)] na [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é criar uma classe que herda de <xref:System.Activities.Activity> que cria funcionalidade montando personalizado atividades ou atividades do [biblioteca de atividades internas ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="6c14d-103">The most basic way to create an activity using [!INCLUDE[wf](../../../includes/wf-md.md)] in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="6c14d-104">Este tópico demonstra como criar uma atividade duas mensagens que grava no console.</span><span class="sxs-lookup"><span data-stu-id="6c14d-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="6c14d-105">Para criar uma atividade personalizado utilizando o designer de atividades</span><span class="sxs-lookup"><span data-stu-id="6c14d-105">To create a custom Activity using the activity designer</span></span>  
  
1.  <span data-ttu-id="6c14d-106">Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c14d-106">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c14d-107">Arquivo, Selecione Novo, Projeto.</span><span class="sxs-lookup"><span data-stu-id="6c14d-107">Select File, New, Project.</span></span> <span data-ttu-id="6c14d-108">Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó.</span><span class="sxs-lookup"><span data-stu-id="6c14d-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="6c14d-109">Selecione **biblioteca de atividades** no **modelos** janela.</span><span class="sxs-lookup"><span data-stu-id="6c14d-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="6c14d-110">Nomeie o novo projeto HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="6c14d-110">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="6c14d-111">Abra a nova atividade.</span><span class="sxs-lookup"><span data-stu-id="6c14d-111">Open the new activity.</span></span>  <span data-ttu-id="6c14d-112">Arraste uma atividade de <xref:System.Activities.Statements.Sequence> da caixa de ferramentas para a superfície de designer.</span><span class="sxs-lookup"><span data-stu-id="6c14d-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>  
  
4.  <span data-ttu-id="6c14d-113">Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> na atividade de <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="6c14d-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="6c14d-114">Digite `"Hello World"` (entre aspas) para o **texto** campo.</span><span class="sxs-lookup"><span data-stu-id="6c14d-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>  
  
5.  <span data-ttu-id="6c14d-115">Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> de segundo na atividade de <xref:System.Activities.Statements.Sequence> , abaixo da primeira.</span><span class="sxs-lookup"><span data-stu-id="6c14d-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="6c14d-116">Digite `"Goodbye"` (entre aspas) para o **texto** campo.</span><span class="sxs-lookup"><span data-stu-id="6c14d-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
