---
title: "Modo de arquivo inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
dev_langs:
- VB
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
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
ms.openlocfilehash: 5eb55d71dca526b859af32355c6731c4c599775e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bad-file-mode"></a><span data-ttu-id="8c8ab-102">Modo de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="8c8ab-102">Bad file mode</span></span>
<span data-ttu-id="8c8ab-103">Instruções usadas para manipular o conteúdo do arquivo devem ser apropriadas para o modo no qual o arquivo foi aberto.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="8c8ab-104">Possíveis causas incluem:</span><span class="sxs-lookup"><span data-stu-id="8c8ab-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="8c8ab-105">A `FilePutObject` ou `FileGetObject` declaração especifica um arquivo sequencial.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="8c8ab-106">A `Print` declaração especifica um arquivo aberto para um modo de acesso diferente de `Output` ou `Append`.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="8c8ab-107">Um `Input` declaração especifica um arquivo aberto para um modo de acesso diferente de`Input`</span><span class="sxs-lookup"><span data-stu-id="8c8ab-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="8c8ab-108">Uma tentativa de gravar em um arquivo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c8ab-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8c8ab-109">To correct this error</span></span>  
  
-   <span data-ttu-id="8c8ab-110">Certifique-se de `FilePutObject` e `FileGetObject` estão se referindo apenas a arquivos abertos para `Random` ou `Binary` acesso.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="8c8ab-111">Certifique-se de `Print` Especifica um arquivo aberto para ou `Output` ou `Append` modo de acesso.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="8c8ab-112">Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabra o arquivo no modo apropriado.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="8c8ab-113">Certifique-se de `Input` Especifica um arquivo aberto para `Input`.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="8c8ab-114">Caso contrário, use uma declaração diferente para colocar dados no arquivo ou reabra o arquivo no modo apropriado.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="8c8ab-115">Se você estiver escrevendo em um arquivo somente leitura, alterar o status de leitura/gravação do arquivo ou não tentar gravar nele.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="8c8ab-116">Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="8c8ab-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8ab-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c8ab-117">See Also</span></span>  
 <span data-ttu-id="8c8ab-118"><xref:Microsoft.VisualBasic.FileSystem></xref:Microsoft.VisualBasic.FileSystem></span><span class="sxs-lookup"><span data-stu-id="8c8ab-118"><xref:Microsoft.VisualBasic.FileSystem></span></span>   
<span data-ttu-id="8c8ab-119"> [Solução de problemas: lendo e gravando em arquivos de texto](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)</span><span class="sxs-lookup"><span data-stu-id="8c8ab-119"> [Troubleshooting: Reading from and Writing to Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)</span></span>
