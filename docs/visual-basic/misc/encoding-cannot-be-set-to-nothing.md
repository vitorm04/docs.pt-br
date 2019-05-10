---
title: Codificação não pode ser definida como Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 492db7755e8b2b75ea8c60d7f4e1ccc1a5ded865
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598360"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="947a4-102">Codificação não pode ser definida como Nothing</span><span class="sxs-lookup"><span data-stu-id="947a4-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="947a4-103">Falha ao tentar ler ou gravar em um arquivo porque o parâmetro `encoding` foi definida como `Nothing` , mas requer um valor válido.</span><span class="sxs-lookup"><span data-stu-id="947a4-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="947a4-104"><xref:System.Text.Encoding> é usado para determinar a codificação a ser usada ao gravar em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="947a4-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="947a4-105">O padrão é UTF-8.</span><span class="sxs-lookup"><span data-stu-id="947a4-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="947a4-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="947a4-106">To correct this error</span></span>  
  
- <span data-ttu-id="947a4-107">Forneça um valor válido para o `encoding` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="947a4-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947a4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="947a4-108">See also</span></span>

- [<span data-ttu-id="947a4-109">Codificações de Arquivo</span><span class="sxs-lookup"><span data-stu-id="947a4-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="947a4-110">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="947a4-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="947a4-111">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="947a4-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="947a4-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="947a4-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="947a4-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="947a4-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
