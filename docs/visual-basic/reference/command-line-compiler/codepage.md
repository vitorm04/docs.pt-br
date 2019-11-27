---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: a38fb4be9347b3372b4a459fce2e96b9e38c3a51
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343540"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="8634a-102">-CodePage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8634a-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="8634a-103">Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="8634a-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8634a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8634a-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="8634a-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="8634a-105">Arguments</span></span>  
  
|<span data-ttu-id="8634a-106">Termo</span><span class="sxs-lookup"><span data-stu-id="8634a-106">Term</span></span>|<span data-ttu-id="8634a-107">Definição</span><span class="sxs-lookup"><span data-stu-id="8634a-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="8634a-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8634a-108">Required.</span></span> <span data-ttu-id="8634a-109">O compilador usa a página de código especificada por `id` para interpretar a codificação dos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="8634a-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8634a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8634a-110">Remarks</span></span>  
 <span data-ttu-id="8634a-111">Para compilar o código-fonte salvo com uma codificação específica, você pode usar `-codepage` para especificar qual página de código deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="8634a-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="8634a-112">A opção `-codepage` se aplica a todos os arquivos de código-fonte em sua compilação.</span><span class="sxs-lookup"><span data-stu-id="8634a-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="8634a-113">Para obter mais informações, consulte [codificação de caracteres no .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="8634a-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="8634a-114">A opção `-codepage` não será necessária se os arquivos de código-fonte tiverem sido salvos usando a página de código ANSI atual, o Unicode ou o UTF-8 com uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="8634a-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="8634a-115">O Visual Studio salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação na caixa de diálogo **codificação** .</span><span class="sxs-lookup"><span data-stu-id="8634a-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="8634a-116">O Visual Studio usa a caixa de diálogo **codificação** para abrir arquivos de código-fonte salvos com uma página de código diferente.</span><span class="sxs-lookup"><span data-stu-id="8634a-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8634a-117">A opção `-codepage` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8634a-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8634a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8634a-118">See also</span></span>

- [<span data-ttu-id="8634a-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8634a-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
