---
title: A codificação não pode ser definida como Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 0356098ca3fb41804ea396b0ff792cf2990b3340
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077534"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="bb5a9-102">A codificação não pode ser definida como Nothing</span><span class="sxs-lookup"><span data-stu-id="bb5a9-102">Encoding cannot be set to Nothing</span></span>

<span data-ttu-id="bb5a9-103">Falha na tentativa de ler ou gravar em um arquivo porque o parâmetro foi `encoding` definido como `Nothing` , mas requer um valor válido.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="bb5a9-104"><xref:System.Text.Encoding> é usado para determinar qual codificação usar ao gravar em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="bb5a9-105">O padrão é UTF-8.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb5a9-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bb5a9-106">To correct this error</span></span>  
  
- <span data-ttu-id="bb5a9-107">Forneça um valor válido para o `encoding` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bb5a9-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5a9-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb5a9-108">See also</span></span>

- [<span data-ttu-id="bb5a9-109">Codificações de arquivo</span><span class="sxs-lookup"><span data-stu-id="bb5a9-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="bb5a9-110">Ler arquivos</span><span class="sxs-lookup"><span data-stu-id="bb5a9-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="bb5a9-111">Gravar em arquivos</span><span class="sxs-lookup"><span data-stu-id="bb5a9-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="bb5a9-112">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="bb5a9-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="bb5a9-113">My. Computer. FileSystem. WriteAllText</span><span class="sxs-lookup"><span data-stu-id="bb5a9-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
