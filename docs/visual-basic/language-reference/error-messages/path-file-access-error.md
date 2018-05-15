---
title: Erro ao acessar arquivo de caminho
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="pathfile-access-error"></a><span data-ttu-id="80d5f-102">Erro de acesso ao demarcador/arquivo</span><span class="sxs-lookup"><span data-stu-id="80d5f-102">Path/File access error</span></span>
<span data-ttu-id="80d5f-103">Durante uma operação de acesso a arquivos ou o acesso ao disco, o sistema operacional não pôde fazer uma conexão entre o caminho e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="80d5f-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80d5f-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="80d5f-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="80d5f-105">Verifique se que a especificação de arquivo está formatada corretamente.</span><span class="sxs-lookup"><span data-stu-id="80d5f-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="80d5f-106">Um nome de arquivo pode conter um (absoluto) totalmente qualificado ou relativo ao caminho.</span><span class="sxs-lookup"><span data-stu-id="80d5f-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="80d5f-107">Um caminho totalmente qualificado inicia com o nome da unidade (se o caminho está em outra unidade) e lista o caminho específico da raiz para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="80d5f-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="80d5f-108">Qualquer caminho que não é totalmente qualificado é relativo a unidade atual e a pasta.</span><span class="sxs-lookup"><span data-stu-id="80d5f-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="80d5f-109">Certifique-se de que você não tentou salvar um arquivo que substitua um arquivo existente de somente leitura.</span><span class="sxs-lookup"><span data-stu-id="80d5f-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="80d5f-110">Se esse for o caso, altere o atributo somente leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.</span><span class="sxs-lookup"><span data-stu-id="80d5f-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="80d5f-111">Certifique-se de que não houve tentativa de abrir um arquivo somente leitura em sequencial `Output` ou `Append` modo.</span><span class="sxs-lookup"><span data-stu-id="80d5f-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="80d5f-112">Se esse for o caso, abra o arquivo no `Input` modo ou alterar o atributo somente leitura do arquivo.</span><span class="sxs-lookup"><span data-stu-id="80d5f-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="80d5f-113">Certifique-se de que não houve tentativa de alterar um projeto do Visual Basic dentro de um banco de dados ou documento.</span><span class="sxs-lookup"><span data-stu-id="80d5f-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d5f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80d5f-114">See Also</span></span>  
 [<span data-ttu-id="80d5f-115">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="80d5f-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
