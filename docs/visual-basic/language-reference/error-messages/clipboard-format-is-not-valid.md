---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649862"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="67bcc-102">Formato inválido de área de transferência</span><span class="sxs-lookup"><span data-stu-id="67bcc-102">Clipboard format is not valid</span></span>
<span data-ttu-id="67bcc-103">O formato da área de transferência especificado é incompatível com o método que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="67bcc-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="67bcc-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="67bcc-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="67bcc-105">Usando a área de transferência `GetText` ou `SetText` método com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink`.</span><span class="sxs-lookup"><span data-stu-id="67bcc-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
- <span data-ttu-id="67bcc-106">Usando a área de transferência `GetData` ou `SetData` método com um formato de área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.</span><span class="sxs-lookup"><span data-stu-id="67bcc-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
- <span data-ttu-id="67bcc-107">Usando o `GetData` ou `SetData` métodos de um `DataObject` com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para registrado formatos (& HC000 - HFFFF &), quando esse formato de área de transferência não foi registrado com o Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="67bcc-107">Using the `GetData` or `SetData` methods of a `DataObject` with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67bcc-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="67bcc-108">To correct this error</span></span>  
  
- <span data-ttu-id="67bcc-109">Remova o formato inválido e especifique um válido.</span><span class="sxs-lookup"><span data-stu-id="67bcc-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67bcc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67bcc-110">See also</span></span>

- [<span data-ttu-id="67bcc-111">Área de transferência: adicionar outros formatos</span><span class="sxs-lookup"><span data-stu-id="67bcc-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
