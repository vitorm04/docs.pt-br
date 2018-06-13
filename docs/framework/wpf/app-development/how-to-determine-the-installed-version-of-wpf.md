---
title: Como determinar a versão instalada do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545845"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="b2652-102">Como determinar a versão instalada do WPF</span><span class="sxs-lookup"><span data-stu-id="b2652-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="b2652-103">O número de versão para a versão atual instalada do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] está localizado no **registro**.</span><span class="sxs-lookup"><span data-stu-id="b2652-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="b2652-104">Para localizar o número de versão:</span><span class="sxs-lookup"><span data-stu-id="b2652-104">To find the version number:</span></span>  
  
1.  <span data-ttu-id="b2652-105">No menu **Iniciar** , clique em **Executar**.</span><span class="sxs-lookup"><span data-stu-id="b2652-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="b2652-106">Em **abrir**, tipo **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="b2652-106">In **Open**, type **regedit.exe**.</span></span>  
  
3.  <span data-ttu-id="b2652-107">Abra a seguinte chave:</span><span class="sxs-lookup"><span data-stu-id="b2652-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="b2652-108">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o número de versão é armazenado no **versão** valor.</span><span class="sxs-lookup"><span data-stu-id="b2652-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
