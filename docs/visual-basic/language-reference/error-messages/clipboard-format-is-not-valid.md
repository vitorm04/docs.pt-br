---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817169"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="ea52d-102">Formato inválido de área de transferência</span><span class="sxs-lookup"><span data-stu-id="ea52d-102">Clipboard format is not valid</span></span>
<span data-ttu-id="ea52d-103">O formato da área de transferência especificado é incompatível com o método que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ea52d-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="ea52d-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="ea52d-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="ea52d-105">Usando a área de transferência `GetText` ou `SetText` método com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="ea52d-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="ea52d-106">Usando a área de transferência `GetData` ou `SetData` método com um formato de área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="ea52d-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="ea52d-107">Usando o `GetData` ou `SetData` métodos de um `DataObject` com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para registrado formatos (& HC000 - HFFFF &), quando esse formato de área de transferência não foi registrado com o Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="ea52d-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ea52d-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ea52d-108">To correct this error</span></span>  
  
-   <span data-ttu-id="ea52d-109">Remova o formato inválido e especifique um válido.</span><span class="sxs-lookup"><span data-stu-id="ea52d-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea52d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea52d-110">See also</span></span>

- [<span data-ttu-id="ea52d-111">Área de transferência: Adicionando outros formatos</span><span class="sxs-lookup"><span data-stu-id="ea52d-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
