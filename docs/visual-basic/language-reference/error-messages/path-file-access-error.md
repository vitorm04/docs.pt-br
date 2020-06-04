---
title: Erro de acesso ao demarcador/arquivo
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387251"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="ccf39-102">Erro de acesso ao demarcador/arquivo</span><span class="sxs-lookup"><span data-stu-id="ccf39-102">Path/File access error</span></span>
<span data-ttu-id="ccf39-103">Durante uma operação de acesso a arquivo ou de acesso a disco, o sistema operacional não pôde estabelecer uma conexão entre o caminho e o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ccf39-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ccf39-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ccf39-104">To correct this error</span></span>  
  
1. <span data-ttu-id="ccf39-105">Verifique se a especificação do arquivo está formatada corretamente.</span><span class="sxs-lookup"><span data-stu-id="ccf39-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="ccf39-106">Um nome de arquivo pode conter um caminho totalmente qualificado (absoluto) ou relativo.</span><span class="sxs-lookup"><span data-stu-id="ccf39-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="ccf39-107">Um caminho totalmente qualificado começa com o nome da unidade (se o caminho estiver em outra unidade) e listará o caminho explícito da raiz para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="ccf39-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="ccf39-108">Qualquer caminho que não esteja totalmente qualificado é relativo à unidade e ao diretório atuais.</span><span class="sxs-lookup"><span data-stu-id="ccf39-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="ccf39-109">Certifique-se de que você não tentou salvar um arquivo que substitua um arquivo somente leitura existente.</span><span class="sxs-lookup"><span data-stu-id="ccf39-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="ccf39-110">Se esse for o caso, altere o atributo somente leitura do arquivo de destino ou salve o arquivo com um nome de arquivo diferente.</span><span class="sxs-lookup"><span data-stu-id="ccf39-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="ccf39-111">Certifique-se de que você não tentou abrir um arquivo somente leitura em sequência `Output` ou no `Append` modo.</span><span class="sxs-lookup"><span data-stu-id="ccf39-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="ccf39-112">Se esse for o caso, abra o arquivo no `Input` modo ou altere o atributo somente leitura do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ccf39-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="ccf39-113">Certifique-se de que você não tentou alterar um projeto de Visual Basic dentro de um banco de dados ou documento.</span><span class="sxs-lookup"><span data-stu-id="ccf39-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf39-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ccf39-114">See also</span></span>

- [<span data-ttu-id="ccf39-115">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="ccf39-115">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
