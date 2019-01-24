---
title: Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: 5340c137842591bb1f4408392e02329fb2a491ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651624"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="b57cc-102">Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b57cc-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="b57cc-103">Os três centrais `My` objetos que fornecem funcionalidades de acesso a informações e comumente usadas estão `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), e `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span><span class="sxs-lookup"><span data-stu-id="b57cc-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="b57cc-104">Você pode usar esses objetos para acessar as informações que estão relacionadas ao aplicativo atual, o que o aplicativo está instalado no computador ou o usuário atual do aplicativo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b57cc-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="b57cc-105">My. Application, My. Computer e My. User</span><span class="sxs-lookup"><span data-stu-id="b57cc-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="b57cc-106">Os exemplos a seguir demonstram como informações podem ser recuperados usando `My`.</span><span class="sxs-lookup"><span data-stu-id="b57cc-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 [!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 [!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]  
  
 <span data-ttu-id="b57cc-107">Além de recuperar informações, os membros expostos através desses três objetos também permitem que você executar métodos relacionados a esse objeto.</span><span class="sxs-lookup"><span data-stu-id="b57cc-107">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="b57cc-108">Por exemplo, você pode acessar uma variedade de métodos para manipular arquivos ou atualizar o registro por meio de `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="b57cc-108">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="b57cc-109">E/s de arquivos é significativamente mais fácil e mais rápido com `My`, que inclui uma variedade de métodos e propriedades para manipular arquivos, diretórios e unidades.</span><span class="sxs-lookup"><span data-stu-id="b57cc-109">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="b57cc-110">O <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objeto permite que você leia grandes estruturas de arquivos que têm delimitadas ou campos de largura fixa.</span><span class="sxs-lookup"><span data-stu-id="b57cc-110">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="b57cc-111">Este exemplo abre o `TextFieldParser` `reader` e o usa para ler de `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="b57cc-111">This example opens the `TextFieldParser` `reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]  
  
 <span data-ttu-id="b57cc-112">`My.Application` permite que você alterar a cultura do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b57cc-112">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="b57cc-113">O exemplo a seguir demonstra como esse método pode ser chamado.</span><span class="sxs-lookup"><span data-stu-id="b57cc-113">The following example demonstrates how this method can be called.</span></span>  
  
 [!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b57cc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b57cc-114">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [<span data-ttu-id="b57cc-115">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="b57cc-115">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
