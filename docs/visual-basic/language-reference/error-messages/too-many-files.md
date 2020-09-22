---
title: Muitos arquivos
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: cd168ce86569d2d7558e21a5b4cc5ef385b28313
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873547"
---
# <a name="too-many-files"></a><span data-ttu-id="e1a79-102">Muitos arquivos</span><span class="sxs-lookup"><span data-stu-id="e1a79-102">Too many files</span></span>

<span data-ttu-id="e1a79-103">Mais arquivos foram criados no diretório raiz do que o sistema operacional permite ou mais arquivos foram abertos do que o número especificado na configuração **files =** no arquivo CONFIG.SYS.</span><span class="sxs-lookup"><span data-stu-id="e1a79-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1a79-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e1a79-104">To correct this error</span></span>  
  
1. <span data-ttu-id="e1a79-105">Se o seu programa estiver abrindo, fechando ou salvando arquivos no diretório raiz, altere o programa para que ele use um subdiretório.</span><span class="sxs-lookup"><span data-stu-id="e1a79-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="e1a79-106">Aumente o número de arquivos especificados na configuração **files =** no arquivo CONFIG.SYS e reinicie o computador.</span><span class="sxs-lookup"><span data-stu-id="e1a79-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a79-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1a79-107">See also</span></span>

- [<span data-ttu-id="e1a79-108">Tipos de erro</span><span class="sxs-lookup"><span data-stu-id="e1a79-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
