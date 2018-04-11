---
title: Modo de arquivo inválido
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a><span data-ttu-id="4d1e4-102">Modo de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="4d1e4-102">Bad file mode</span></span>
<span data-ttu-id="4d1e4-103">Instruções usadas na manipulação de conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="4d1e4-104">Possíveis causas incluem:</span><span class="sxs-lookup"><span data-stu-id="4d1e4-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="4d1e4-105">Um `FilePutObject` ou `FileGetObject` instrução Especifica um arquivo sequencial.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="4d1e4-106">Um `Print` declaração especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append`.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="4d1e4-107">Um `Input` declaração especifica um arquivo aberto para um modo de acesso diferente de`Input`</span><span class="sxs-lookup"><span data-stu-id="4d1e4-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="4d1e4-108">Uma tentativa de gravar em um arquivo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d1e4-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4d1e4-109">To correct this error</span></span>  
  
-   <span data-ttu-id="4d1e4-110">Certifique-se de `FilePutObject` e `FileGetObject` somente referindo-se a arquivos abertos para `Random` ou `Binary` acesso.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="4d1e4-111">Certifique-se de `Print` Especifica um arquivo aberto para ou `Output` ou `Append` modo de acesso.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="4d1e4-112">Caso contrário, use uma instrução diferente para colocar dados no arquivo ou reabrir o arquivo no modo apropriado.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="4d1e4-113">Certifique-se de `Input` Especifica um arquivo aberto para `Input`.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="4d1e4-114">Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabrir o arquivo no modo apropriado.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="4d1e4-115">Se você estiver gravando em um arquivo somente leitura, altere o status de leitura/gravação do arquivo ou não tentar gravar nele.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="4d1e4-116">Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="4d1e4-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1e4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d1e4-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [<span data-ttu-id="4d1e4-118">Solução de problemas: lendo e gravando em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="4d1e4-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
