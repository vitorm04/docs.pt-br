---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337234"
---
# <a name="-main"></a><span data-ttu-id="81429-102">-main</span><span class="sxs-lookup"><span data-stu-id="81429-102">-main</span></span>
<span data-ttu-id="81429-103">Especifica a classe ou o módulo que contém o procedimento `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="81429-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81429-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81429-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="81429-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="81429-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="81429-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="81429-106">Required.</span></span> <span data-ttu-id="81429-107">O nome da classe ou módulo que contém o `Sub Main` procedimento a ser chamado quando o programa é iniciado.</span><span class="sxs-lookup"><span data-stu-id="81429-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="81429-108">Isso pode ser na forma **-principal: module** ou **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="81429-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81429-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="81429-109">Remarks</span></span>  
 <span data-ttu-id="81429-110">Use esta opção quando você cria um arquivo executável ou programa executável do Windows.</span><span class="sxs-lookup"><span data-stu-id="81429-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="81429-111">Se o **-principal** opção for omitida, o compilador pesquisa válido compartilhado `Sub Main` em todas as classes públicas e módulos.</span><span class="sxs-lookup"><span data-stu-id="81429-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="81429-112">Ver [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para uma discussão sobre as várias formas dos `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="81429-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="81429-113">Quando `location` é uma classe que herda <xref:System.Windows.Forms.Form>, o compilador fornece um padrão `Main` procedimento que inicia o aplicativo se a classe não tem nenhum `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="81429-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="81429-114">Isso permite que você compilar o código na linha de comando que foi criado no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="81429-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="81429-115">Para definir - principal no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="81429-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="81429-116">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="81429-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="81429-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="81429-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="81429-118">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="81429-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="81429-119">Verifique se o **habilitar estrutura de aplicativo** caixa de seleção não estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="81429-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="81429-120">Modificar o valor de **objeto de inicialização** caixa.</span><span class="sxs-lookup"><span data-stu-id="81429-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81429-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81429-121">Example</span></span>  
 <span data-ttu-id="81429-122">O seguinte código compila `T2.vb` e `T3.vb`, especificando que o `Sub Main` procedimento será encontrado na `Test2` classe.</span><span class="sxs-lookup"><span data-stu-id="81429-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="81429-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81429-123">See also</span></span>

- [<span data-ttu-id="81429-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81429-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="81429-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81429-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="81429-126">Linhas de comando de compilação de exemplo</span><span class="sxs-lookup"><span data-stu-id="81429-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="81429-127">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81429-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
