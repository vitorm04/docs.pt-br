---
title: "Formato da área de transferência não é válido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
dev_langs:
- VB
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6ff866edefcb990b2da8506eb8d9c3566641479e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="bffa9-102">Formato inválido de área de transferência</span><span class="sxs-lookup"><span data-stu-id="bffa9-102">Clipboard format is not valid</span></span>
<span data-ttu-id="bffa9-103">O formato da área de transferência especificado é incompatível com o método que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="bffa9-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="bffa9-104">Entre as possíveis causas para esse erro são:</span><span class="sxs-lookup"><span data-stu-id="bffa9-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="bffa9-105">Usando a área de transferência `GetText` ou `SetText` método com um formato da área de transferência diferente de `vbCFText` ou `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="bffa9-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="bffa9-106">Usando a área de transferência `GetData` ou `SetData` método com um formato da área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="bffa9-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="bffa9-107">Usando o `DataObject``GetData` método ou `SetData` método com um formato da área de transferência no intervalo reservado pelo Microsoft Windows para formatos registrados (< / HC000-< / HFFFF), quando esse formato da área de transferência não foi registrado com o Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="bffa9-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bffa9-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bffa9-108">To correct this error</span></span>  
  
-   <span data-ttu-id="bffa9-109">Remova o formato inválido e especifique um válido.</span><span class="sxs-lookup"><span data-stu-id="bffa9-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffa9-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bffa9-110">See Also</span></span>  
 [<span data-ttu-id="bffa9-111">Área de transferência: adicionando outros formatos</span><span class="sxs-lookup"><span data-stu-id="bffa9-111">Clipboard: Adding Other Formats</span></span>](http://msdn.microsoft.com/library/aea58159-65ed-4385-aeaa-3d9d5281903b)
