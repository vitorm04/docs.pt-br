---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005500"
---
# <a name="-main"></a><span data-ttu-id="eb6eb-102">-main</span><span class="sxs-lookup"><span data-stu-id="eb6eb-102">-main</span></span>
<span data-ttu-id="eb6eb-103">Especifica a classe ou o módulo que contém o procedimento `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb6eb-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb6eb-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="eb6eb-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="eb6eb-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-106">Required.</span></span> <span data-ttu-id="eb6eb-107">O nome da classe ou do módulo que contém o procedimento `Sub Main` a ser chamado quando o programa é iniciado.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="eb6eb-108">Isso pode estar no formato **-principal: módulo** ou **-principal: namespace. Module**.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb6eb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb6eb-109">Remarks</span></span>  
 <span data-ttu-id="eb6eb-110">Use essa opção quando você criar um arquivo executável ou programa executável do Windows.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="eb6eb-111">Se a opção **-Main** for omitida, o compilador pesquisará um `Sub Main` compartilhado válido em todas as classes e módulos públicos.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="eb6eb-112">Consulte o [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para obter uma discussão sobre as várias formas do procedimento `Main`.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="eb6eb-113">Quando `location` é uma classe que herda de <xref:System.Windows.Forms.Form>, o compilador fornece um procedimento padrão `Main` que inicia o aplicativo se a classe não tiver um procedimento `Main`.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="eb6eb-114">Isso permite que você compile o código na linha de comando que foi criada no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="eb6eb-115">Para definir o principal no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eb6eb-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="eb6eb-116">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="eb6eb-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="eb6eb-118">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="eb6eb-119">Verifique se a caixa de seleção **habilitar estrutura de aplicativo** não está marcada.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="eb6eb-120">Modifique o valor na caixa **objeto de inicialização** .</span><span class="sxs-lookup"><span data-stu-id="eb6eb-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb6eb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb6eb-121">Example</span></span>  
 <span data-ttu-id="eb6eb-122">O código a seguir compila `T2.vb` e `T3.vb`, especificando que o procedimento `Sub Main` será encontrado na classe `Test2`.</span><span class="sxs-lookup"><span data-stu-id="eb6eb-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb6eb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb6eb-123">See also</span></span>

- [<span data-ttu-id="eb6eb-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb6eb-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="eb6eb-125">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb6eb-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="eb6eb-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb6eb-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="eb6eb-127">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb6eb-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
