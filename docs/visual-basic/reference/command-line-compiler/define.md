---
title: -Definir (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: d0a483e7a3c9e9863db39e89d655cf172c1e8c81
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649719"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="60951-102">-Definir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60951-102">-define (Visual Basic)</span></span>
<span data-ttu-id="60951-103">Define as constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="60951-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60951-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60951-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="60951-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="60951-105">Arguments</span></span>  
  
|<span data-ttu-id="60951-106">Termo</span><span class="sxs-lookup"><span data-stu-id="60951-106">Term</span></span>|<span data-ttu-id="60951-107">Definição</span><span class="sxs-lookup"><span data-stu-id="60951-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="60951-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="60951-108">Required.</span></span> <span data-ttu-id="60951-109">O símbolo a ser definido.</span><span class="sxs-lookup"><span data-stu-id="60951-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="60951-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="60951-110">Optional.</span></span> <span data-ttu-id="60951-111">O valor para atribuir `symbol`.</span><span class="sxs-lookup"><span data-stu-id="60951-111">The value to assign `symbol`.</span></span> <span data-ttu-id="60951-112">Se `value` é uma cadeia de caracteres, ele deverá ser colocado entre sequências de barra invertida/aspas (\\") em vez de aspas.</span><span class="sxs-lookup"><span data-stu-id="60951-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="60951-113">Se nenhum valor for especificado, será considerado como True.</span><span class="sxs-lookup"><span data-stu-id="60951-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60951-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="60951-114">Remarks</span></span>  
 <span data-ttu-id="60951-115">O `-define` opção tem um efeito semelhante ao uso de um `#Const` diretiva de pré-processador em seu arquivo de origem, exceto que as constantes definidas com `-define` são públicos e se aplicam a todos os arquivos no projeto.</span><span class="sxs-lookup"><span data-stu-id="60951-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="60951-116">Você pode usar símbolos criados por essa opção com a diretiva `#If`...`Then`...`#Else` para compilar os arquivos de origem condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="60951-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="60951-117">`-d` é a forma abreviada de `-define`.</span><span class="sxs-lookup"><span data-stu-id="60951-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="60951-118">Você pode definir vários símbolos com `-define` usando uma vírgula para separar as definições de símbolos.</span><span class="sxs-lookup"><span data-stu-id="60951-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="60951-119">Para configurar /define no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60951-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="60951-120">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="60951-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="60951-121">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="60951-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="60951-122">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="60951-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="60951-123">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="60951-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="60951-124">4.  Modificar o valor de **constantes personalizadas** caixa.</span><span class="sxs-lookup"><span data-stu-id="60951-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="60951-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60951-125">Example</span></span>  
 <span data-ttu-id="60951-126">O código a seguir define e usa duas constantes de compilador condicional.</span><span class="sxs-lookup"><span data-stu-id="60951-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="60951-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60951-127">See also</span></span>

- [<span data-ttu-id="60951-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60951-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="60951-129">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="60951-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="60951-130">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="60951-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="60951-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="60951-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
