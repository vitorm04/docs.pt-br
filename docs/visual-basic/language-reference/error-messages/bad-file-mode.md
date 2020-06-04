---
title: Modo de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409863"
---
# <a name="bad-file-mode"></a><span data-ttu-id="554b9-102">Modo de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="554b9-102">Bad file mode</span></span>
<span data-ttu-id="554b9-103">As instruções usadas na manipulação do conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto.</span><span class="sxs-lookup"><span data-stu-id="554b9-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="554b9-104">As possíveis causas incluem:</span><span class="sxs-lookup"><span data-stu-id="554b9-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="554b9-105">Uma `FilePutObject` `FileGetObject` instrução or especifica um arquivo sequencial.</span><span class="sxs-lookup"><span data-stu-id="554b9-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="554b9-106">Uma `Print` instrução especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append` .</span><span class="sxs-lookup"><span data-stu-id="554b9-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="554b9-107">Uma `Input` instrução especifica um arquivo aberto para um modo de acesso diferente de`Input`</span><span class="sxs-lookup"><span data-stu-id="554b9-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="554b9-108">Uma tentativa de gravar em um arquivo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="554b9-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="554b9-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="554b9-109">To correct this error</span></span>  
  
- <span data-ttu-id="554b9-110">Certifique-se de que `FilePutObject` e `FileGetObject` estão apenas se referindo a arquivos abertos para o `Random` ou o `Binary` Access.</span><span class="sxs-lookup"><span data-stu-id="554b9-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="554b9-111">Certifique-se `Print` de especificar um arquivo aberto para o `Output` modo de `Append` acesso ou.</span><span class="sxs-lookup"><span data-stu-id="554b9-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="554b9-112">Caso contrário, use uma instrução diferente para inserir dados no arquivo ou reabra o arquivo em um modo apropriado.</span><span class="sxs-lookup"><span data-stu-id="554b9-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="554b9-113">Certifique-se `Input` de especificar um arquivo aberto para `Input` .</span><span class="sxs-lookup"><span data-stu-id="554b9-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="554b9-114">Caso contrário, use uma instrução diferente para inserir dados no arquivo ou reabra o arquivo em um modo apropriado.</span><span class="sxs-lookup"><span data-stu-id="554b9-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="554b9-115">Se você estiver gravando em um arquivo somente leitura, altere o status de leitura/gravação do arquivo ou não tente gravar nele.</span><span class="sxs-lookup"><span data-stu-id="554b9-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="554b9-116">Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="554b9-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554b9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="554b9-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="554b9-118">Solução de problemas: ler e gravar em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="554b9-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
