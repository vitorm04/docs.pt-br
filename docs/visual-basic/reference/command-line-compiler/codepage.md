---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8aee51df3ba9f92ca662fbbfbd73998e4a3b4538
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882598"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="64aa6-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64aa6-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="64aa6-103">Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="64aa6-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64aa6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64aa6-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="64aa6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64aa6-105">Arguments</span></span>  
  
|<span data-ttu-id="64aa6-106">Termo</span><span class="sxs-lookup"><span data-stu-id="64aa6-106">Term</span></span>|<span data-ttu-id="64aa6-107">Definição</span><span class="sxs-lookup"><span data-stu-id="64aa6-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="64aa6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="64aa6-108">Required.</span></span> <span data-ttu-id="64aa6-109">O compilador usa a página de código especificada pelo `id` para interpretar a codificação dos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="64aa6-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64aa6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="64aa6-110">Remarks</span></span>  
 <span data-ttu-id="64aa6-111">Para compilar o código-fonte salvo com uma codificação específica, você pode usar `-codepage` para especificar qual página de código deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="64aa6-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="64aa6-112">O `-codepage` opção se aplica a todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="64aa6-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="64aa6-113">Para obter mais informações, consulte [codificação de caracteres no .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="64aa6-113">For more information, see [Character Encoding in the .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="64aa6-114">O `-codepage` opção não será necessária se os arquivos de código-fonte foram salvos com a página de código ANSI atual, Unicode ou UTF-8 com uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="64aa6-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="64aa6-115">O Visual Studio salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação na **Encoding** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="64aa6-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="64aa6-116">O Visual Studio usa o **Encoding** caixa de diálogo para abrir arquivos de código-fonte salvos com uma página de código diferente.</span><span class="sxs-lookup"><span data-stu-id="64aa6-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64aa6-117">O `-codepage` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="64aa6-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64aa6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64aa6-118">See Also</span></span>  
 [<span data-ttu-id="64aa6-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64aa6-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
