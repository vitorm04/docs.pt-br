---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874586"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="1e4c1-102">Formato inválido de área de transferência</span><span class="sxs-lookup"><span data-stu-id="1e4c1-102">Clipboard format is not valid</span></span>

<span data-ttu-id="1e4c1-103">O formato da área de transferência especificado é incompatível com o método que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="1e4c1-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="1e4c1-104">Entre as possíveis causas desse erro estão:</span><span class="sxs-lookup"><span data-stu-id="1e4c1-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="1e4c1-105">Usando o método ou da área de transferência `GetText` `SetText` com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink` .</span><span class="sxs-lookup"><span data-stu-id="1e4c1-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="1e4c1-106">Usando o método ou da área de transferência `GetData` `SetData` com um formato de área de transferência diferente de `vbCFBitmap` , `vbCFDIB` ou `vbCFMetafile` .</span><span class="sxs-lookup"><span data-stu-id="1e4c1-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="1e4c1-107">Usando os `GetData` `SetData` métodos ou de um `DataObject` com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para formatos registrados (&HC000-&HFFFF), quando esse formato de área de transferência não foi registrado no Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="1e4c1-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e4c1-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1e4c1-108">To correct this error</span></span>  
  
- <span data-ttu-id="1e4c1-109">Remova o formato inválido e especifique um válido.</span><span class="sxs-lookup"><span data-stu-id="1e4c1-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4c1-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e4c1-110">See also</span></span>

- [<span data-ttu-id="1e4c1-111">Área de transferência: adicionando outros formatos</span><span class="sxs-lookup"><span data-stu-id="1e4c1-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
