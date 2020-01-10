---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5035466de4aa17c374824e1b0f02ed594731a9d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716806"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="8aaf2-102">-definir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8aaf2-102">-define (Visual Basic)</span></span>
<span data-ttu-id="8aaf2-103">Define as constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aaf2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8aaf2-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="8aaf2-105">ou</span><span class="sxs-lookup"><span data-stu-id="8aaf2-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8aaf2-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="8aaf2-106">Arguments</span></span>  
  
|<span data-ttu-id="8aaf2-107">Termo</span><span class="sxs-lookup"><span data-stu-id="8aaf2-107">Term</span></span>|<span data-ttu-id="8aaf2-108">Definição</span><span class="sxs-lookup"><span data-stu-id="8aaf2-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="8aaf2-109">Necessária.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-109">Required.</span></span> <span data-ttu-id="8aaf2-110">O símbolo a ser definido.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="8aaf2-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-111">Optional.</span></span> <span data-ttu-id="8aaf2-112">O valor para atribuir `symbol`.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-112">The value to assign `symbol`.</span></span> <span data-ttu-id="8aaf2-113">Se `value` for uma cadeia de caracteres, ela deverá ser cercada por sequências de barra invertida/aspas (\\") em vez de aspas.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="8aaf2-114">Se nenhum valor for especificado, será considerado como True.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aaf2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8aaf2-115">Remarks</span></span>  
 <span data-ttu-id="8aaf2-116">A opção `-define` tem um efeito semelhante a usar uma diretiva de pré-processador de `#Const` em seu arquivo de origem, exceto que as constantes definidas com `-define` são públicas e se aplicam a todos os arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="8aaf2-117">Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="8aaf2-118">`-d` é a forma abreviada de `-define`.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="8aaf2-119">Você pode definir vários símbolos com `-define` usando uma vírgula para separar as definições de símbolos.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="8aaf2-120">Para definir-definir no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8aaf2-120">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8aaf2-121">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8aaf2-122">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8aaf2-123">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="8aaf2-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8aaf2-124">3. clique em **avançado**.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="8aaf2-125">4. modifique o valor na caixa **constantes personalizadas** .</span><span class="sxs-lookup"><span data-stu-id="8aaf2-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8aaf2-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8aaf2-126">Example</span></span>  
 <span data-ttu-id="8aaf2-127">O código a seguir define e usa duas constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="8aaf2-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="8aaf2-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="8aaf2-128">See also</span></span>

- [<span data-ttu-id="8aaf2-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8aaf2-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8aaf2-130">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="8aaf2-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="8aaf2-131">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="8aaf2-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="8aaf2-132">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="8aaf2-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
