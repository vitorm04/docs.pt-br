---
title: -codepage (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 04a0d3a62ebd2b3a938445995725994d72d5bd4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216919"
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="ae08d-102">-codepage (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ae08d-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="ae08d-103">Esta opção especifica qual página de código deve ser usada durante a compilação caso a página necessária não seja a página de código padrão atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="ae08d-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae08d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae08d-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae08d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae08d-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="ae08d-106">Especifica a ID da página de código a ser usada para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="ae08d-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae08d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae08d-107">Remarks</span></span>  
 <span data-ttu-id="ae08d-108">Se um ou mais arquivos de código-fonte que não foram criados para usar a página de código padrão no computador forem compilados, será possível usar a opção **-codepage** para especificar qual página de código deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="ae08d-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="ae08d-109">**-codepage** se aplica a todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="ae08d-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="ae08d-110">Caso os arquivos de código-fonte tiverem sido criados com a mesma página de código em uso no seu computador, com UNICODE ou com UTF-8, não será necessário usar **-codepage**.</span><span class="sxs-lookup"><span data-stu-id="ae08d-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="ae08d-111">Consulte [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) para obter informações sobre como localizar quais páginas de código têm suporte do sistema.</span><span class="sxs-lookup"><span data-stu-id="ae08d-111">See [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="ae08d-112">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="ae08d-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae08d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae08d-113">See Also</span></span>  
 [<span data-ttu-id="ae08d-114">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="ae08d-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ae08d-115">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="ae08d-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
