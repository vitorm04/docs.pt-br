---
title: Determinar a versão instalada do WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: 8fc5c380779891b44b7c4f7f8aeb5ed119d8b768
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735688"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="e6cc8-102">Como determinar a versão instalada do WPF</span><span class="sxs-lookup"><span data-stu-id="e6cc8-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="e6cc8-103">O número de versão da versão instalada atual do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] está localizado no **registro**.</span><span class="sxs-lookup"><span data-stu-id="e6cc8-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="e6cc8-104">Para localizar o número de versão:</span><span class="sxs-lookup"><span data-stu-id="e6cc8-104">To find the version number:</span></span>  
  
1. <span data-ttu-id="e6cc8-105">No menu **Iniciar** , clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="e6cc8-105">On the **Start** menu, click **Run**.</span></span>  
  
2. <span data-ttu-id="e6cc8-106">Em **abrir**, digite **regedit. exe**.</span><span class="sxs-lookup"><span data-stu-id="e6cc8-106">In **Open**, type **regedit.exe**.</span></span>  
  
3. <span data-ttu-id="e6cc8-107">Abra a seguinte chave:</span><span class="sxs-lookup"><span data-stu-id="e6cc8-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="e6cc8-108">O número de versão de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é armazenado no valor de **versão** .</span><span class="sxs-lookup"><span data-stu-id="e6cc8-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
