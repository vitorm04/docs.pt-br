---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524474"
---
# <a name="-addmodule"></a><span data-ttu-id="a78c4-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="a78c4-102">-addmodule</span></span>
<span data-ttu-id="a78c4-103">Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.</span><span class="sxs-lookup"><span data-stu-id="a78c4-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a78c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a78c4-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="a78c4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a78c4-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="a78c4-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a78c4-106">Required.</span></span> <span data-ttu-id="a78c4-107">Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos de assembly.</span><span class="sxs-lookup"><span data-stu-id="a78c4-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="a78c4-108">Os nomes de arquivo que contêm espaços devem estar entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="a78c4-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a78c4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a78c4-109">Remarks</span></span>  
 <span data-ttu-id="a78c4-110">Os arquivos listados pelo parâmetro `fileList` devem ser criados com a opção `-target:module` ou com um equivalente de `-target:module` do compilador.</span><span class="sxs-lookup"><span data-stu-id="a78c4-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="a78c4-111">Todos os módulos adicionados com `-addmodule` devem estar no mesmo diretório que o arquivo de saída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a78c4-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="a78c4-112">Ou seja, você pode especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a78c4-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="a78c4-113">Se não estiver, você receberá um erro de <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="a78c4-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="a78c4-114">Se você especificar (implícita ou explicitamente) qualquer opção[-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) diferente de `-target:module` com `-addmodule`, os arquivos passados para `-addmodule` se tornarão parte do assembly do projeto.</span><span class="sxs-lookup"><span data-stu-id="a78c4-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="a78c4-115">Um assembly é necessário para executar um arquivo de saída que tenha um ou mais arquivos adicionados com `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="a78c4-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="a78c4-116">Use [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) para importar metadados de um arquivo que contém um assembly.</span><span class="sxs-lookup"><span data-stu-id="a78c4-116">Use [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a78c4-117">A opção `-addmodule` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a78c4-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a78c4-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a78c4-118">Example</span></span>  
 <span data-ttu-id="a78c4-119">O código a seguir cria um módulo.</span><span class="sxs-lookup"><span data-stu-id="a78c4-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="a78c4-120">O código a seguir importa os tipos do módulo.</span><span class="sxs-lookup"><span data-stu-id="a78c4-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="a78c4-121">Quando você executa `t1`, ele gera `802`.</span><span class="sxs-lookup"><span data-stu-id="a78c4-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78c4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a78c4-122">See also</span></span>

- [<span data-ttu-id="a78c4-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a78c4-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a78c4-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a78c4-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="a78c4-125">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a78c4-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="a78c4-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="a78c4-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
