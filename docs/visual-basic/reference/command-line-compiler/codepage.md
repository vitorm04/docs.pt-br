---
title: -página de código (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 736b35f51657aa7b21a6a077d70f5e9ff0d4fb85
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="7716e-102">-página de código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7716e-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="7716e-103">Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="7716e-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7716e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7716e-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="7716e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7716e-105">Arguments</span></span>  
  
|<span data-ttu-id="7716e-106">Termo</span><span class="sxs-lookup"><span data-stu-id="7716e-106">Term</span></span>|<span data-ttu-id="7716e-107">Definição</span><span class="sxs-lookup"><span data-stu-id="7716e-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="7716e-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7716e-108">Required.</span></span> <span data-ttu-id="7716e-109">O compilador usa a página de código especificada por `id` para interpretar a codificação dos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="7716e-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7716e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7716e-110">Remarks</span></span>  
 <span data-ttu-id="7716e-111">Para compilar o código-fonte salvo com uma codificação específica, você pode usar `-codepage` para especificar a página de código deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="7716e-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="7716e-112">O `-codepage` opção se aplica a todos os arquivos de código-fonte na sua compilação.</span><span class="sxs-lookup"><span data-stu-id="7716e-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="7716e-113">Para obter mais informações, consulte [codificação de caracteres no .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="7716e-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="7716e-114">O `-codepage` opção não é necessária se os arquivos de código-fonte foram salvos com a página de código ANSI atual, Unicode ou UTF-8 com uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="7716e-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="7716e-115"> salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação no **codificação** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7716e-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="7716e-116"> usa o **codificação** caixa de diálogo para abrir arquivos de código-fonte salvos com uma página de código diferente.</span><span class="sxs-lookup"><span data-stu-id="7716e-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7716e-117">O `-codepage` opção não está disponível de dentro do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ambiente de desenvolvimento; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7716e-117">The `-codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7716e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7716e-118">See Also</span></span>  
 [<span data-ttu-id="7716e-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7716e-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
