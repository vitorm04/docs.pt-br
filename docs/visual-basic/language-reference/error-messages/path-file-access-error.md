---
title: Erro ao acessar arquivo de caminho | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
dev_langs:
- VB
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
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
ms.openlocfilehash: 6307c0d0115e3791d5ad6bf4243057e6ed90d9cd
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="pathfile-access-error"></a><span data-ttu-id="a7d68-102">Erro de acesso ao demarcador/arquivo</span><span class="sxs-lookup"><span data-stu-id="a7d68-102">Path/File access error</span></span>
<span data-ttu-id="a7d68-103">Durante uma operação de acesso a arquivos ou acesso ao disco, o sistema operacional não pôde fazer uma conexão entre o caminho e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="a7d68-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7d68-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a7d68-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a7d68-105">Verifique se que a especificação de arquivo está formatada corretamente.</span><span class="sxs-lookup"><span data-stu-id="a7d68-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="a7d68-106">Um nome de arquivo pode conter um (absoluto) totalmente qualificado ou relativo ao caminho.</span><span class="sxs-lookup"><span data-stu-id="a7d68-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="a7d68-107">Um caminho totalmente qualificado inicia com o nome da unidade (se o caminho estiver em outra unidade) e lista o caminho específico da raiz no arquivo.</span><span class="sxs-lookup"><span data-stu-id="a7d68-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="a7d68-108">Qualquer caminho que não é totalmente qualificado é relativo a unidade atual e o diretório.</span><span class="sxs-lookup"><span data-stu-id="a7d68-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="a7d68-109">Certifique-se de que você não tentou salvar um arquivo que substituiria um arquivo somente leitura existente.</span><span class="sxs-lookup"><span data-stu-id="a7d68-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="a7d68-110">Se esse for o caso, altere o atributo somente leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.</span><span class="sxs-lookup"><span data-stu-id="a7d68-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="a7d68-111">Verifique se você não tentou abrir um arquivo somente leitura no sequencial`Output`ou `Append` modo.</span><span class="sxs-lookup"><span data-stu-id="a7d68-111">Make sure you did not attempt to open a read-only file in sequential`Output`or `Append` mode.</span></span> <span data-ttu-id="a7d68-112">Se esse for o caso, abra o arquivo no `Input` modo ou alterar o atributo somente leitura do arquivo.</span><span class="sxs-lookup"><span data-stu-id="a7d68-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="a7d68-113">Verifique se você não tentou alterar uma [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto dentro de um banco de dados ou documento.</span><span class="sxs-lookup"><span data-stu-id="a7d68-113">Make sure you did not attempt to change a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d68-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7d68-114">See Also</span></span>  
 [<span data-ttu-id="a7d68-115">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="a7d68-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
