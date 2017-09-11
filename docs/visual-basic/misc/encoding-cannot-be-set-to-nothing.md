---
title: "Codificação não pode ser definida como Nothing | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f1df8159d77275ee23d99a1a85e0625a5183a23c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="c3d3b-102">Codificação não pode ser definida como Nothing</span><span class="sxs-lookup"><span data-stu-id="c3d3b-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="c3d3b-103">Uma tentativa de ler ou gravar em um arquivo falhou porque o parâmetro `encoding` foi definido como `Nothing` , mas requer um valor válido.</span><span class="sxs-lookup"><span data-stu-id="c3d3b-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="c3d3b-104"><xref:System.Text.Encoding>é usado para determinar que codificação usar ao gravar em um arquivo.</xref:System.Text.Encoding></span><span class="sxs-lookup"><span data-stu-id="c3d3b-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="c3d3b-105">O padrão é UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c3d3b-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3d3b-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c3d3b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c3d3b-107">Forneça um valor válido para o `encoding` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c3d3b-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d3b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3d3b-108">See Also</span></span>  
 <span data-ttu-id="c3d3b-109">[Codificações de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) </span><span class="sxs-lookup"><span data-stu-id="c3d3b-109">[File Encodings](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) </span></span>  
<span data-ttu-id="c3d3b-110"> [Leitura de arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span><span class="sxs-lookup"><span data-stu-id="c3d3b-110"> [Reading from Files](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span></span>  
<span data-ttu-id="c3d3b-111"> [Gravando em arquivos](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md) </span><span class="sxs-lookup"><span data-stu-id="c3d3b-111"> [Writing to Files](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md) </span></span>  
<span data-ttu-id="c3d3b-112"> [Método ReadAllText](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f) </span><span class="sxs-lookup"><span data-stu-id="c3d3b-112"> [My.Computer.FileSystem.ReadAllText Method](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f) </span></span>  
<span data-ttu-id="c3d3b-113"> [Método WriteAllText](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)</span><span class="sxs-lookup"><span data-stu-id="c3d3b-113"> [My.Computer.FileSystem.WriteAllText Method](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)</span></span>
