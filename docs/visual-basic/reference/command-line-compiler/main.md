---
title: -principal
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b22b4bb1b6649265eabc02beb6b0145f7c075b27
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-main"></a><span data-ttu-id="b1795-102">-principal</span><span class="sxs-lookup"><span data-stu-id="b1795-102">-main</span></span>
<span data-ttu-id="b1795-103">Especifica a classe ou o módulo que contém o procedimento `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="b1795-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1795-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1795-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="b1795-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b1795-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="b1795-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b1795-106">Required.</span></span> <span data-ttu-id="b1795-107">O nome da classe ou módulo que contém o `Sub Main` procedimento a ser chamado quando o programa for iniciado.</span><span class="sxs-lookup"><span data-stu-id="b1795-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="b1795-108">Isso pode estar no formato **-principal: módulo** ou **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="b1795-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1795-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1795-109">Remarks</span></span>  
 <span data-ttu-id="b1795-110">Use esta opção quando você cria um arquivo executável ou programa executável do Windows.</span><span class="sxs-lookup"><span data-stu-id="b1795-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="b1795-111">Se o **-principal** opção for omitida, o compilador procura por válido compartilhado `Sub Main` em todas as classes públicas e módulos.</span><span class="sxs-lookup"><span data-stu-id="b1795-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="b1795-112">Consulte [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para uma discussão sobre as várias formas da `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="b1795-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="b1795-113">Quando `location` é uma classe que herda de <xref:System.Windows.Forms.Form>, o compilador fornece um padrão `Main` procedimento que inicia o aplicativo se a classe não tiver nenhuma `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="b1795-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="b1795-114">Isso permite que você compilar código na linha de comando que foi criado no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b1795-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="b1795-115">Para definir - principal no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b1795-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="b1795-116">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="b1795-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b1795-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b1795-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b1795-118">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="b1795-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="b1795-119">Verifique se o **habilitar estrutura de aplicativo** caixa de seleção não está marcada.</span><span class="sxs-lookup"><span data-stu-id="b1795-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="b1795-120">Modificar o valor de **objeto de inicialização** caixa.</span><span class="sxs-lookup"><span data-stu-id="b1795-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1795-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1795-121">Example</span></span>  
 <span data-ttu-id="b1795-122">O código a seguir compila `T2.vb` e `T3.vb`, especificando que o `Sub Main` procedimento será localizado no `Test2` classe.</span><span class="sxs-lookup"><span data-stu-id="b1795-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1795-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1795-123">See Also</span></span>  
 [<span data-ttu-id="b1795-124">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1795-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b1795-125">-alvo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1795-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="b1795-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1795-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="b1795-127">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1795-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
