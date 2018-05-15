---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="8d8ad-102">Formato inválido de área de transferência</span><span class="sxs-lookup"><span data-stu-id="8d8ad-102">Clipboard format is not valid</span></span>
<span data-ttu-id="8d8ad-103">O formato de área de transferência especificado é incompatível com o método que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="8d8ad-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="8d8ad-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="8d8ad-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="8d8ad-105">Usando a área de transferência `GetText` ou `SetText` método com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="8d8ad-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="8d8ad-106">Usando a área de transferência `GetData` ou `SetData` método com um formato de área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="8d8ad-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="8d8ad-107">Usando o `DataObject``GetData` método ou `SetData` método com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para registrado formatos (& HC000 - HFFFF &), quando esse formato de área de transferência não foi registrado com o Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="8d8ad-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d8ad-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8d8ad-108">To correct this error</span></span>  
  
-   <span data-ttu-id="8d8ad-109">Remova o formato inválido e especifique um válido.</span><span class="sxs-lookup"><span data-stu-id="8d8ad-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8ad-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d8ad-110">See Also</span></span>  
 [<span data-ttu-id="8d8ad-111">Área de transferência: adicionando outros formatos</span><span class="sxs-lookup"><span data-stu-id="8d8ad-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
