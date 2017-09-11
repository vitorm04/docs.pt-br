---
title: Executando tarefas com My. Application, My. Computer e My. User (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application object, developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object, developing applications
- My.User object, developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7d5bd46015567698c49f1181db69f0c39c225c06
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a><span data-ttu-id="ce496-102">Executando tarefas com My.Application, My.Computer e My.User (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce496-102">Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)</span></span>
<span data-ttu-id="ce496-103">Os três centrais `My` são objetos que fornecem acesso às informações e comumente usado funcionalmente `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), e `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</xref:Microsoft.VisualBasic.ApplicationServices.User> </xref:Microsoft.VisualBasic.Devices.Computer> </xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span><span class="sxs-lookup"><span data-stu-id="ce496-103">The three central `My` objects that provide access to information and commonly used functionality are `My.Application` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>), `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), and `My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>).</span></span> <span data-ttu-id="ce496-104">Você pode usar esses objetos para acessar informações relacionadas para o aplicativo atual, que o aplicativo é instalado no computador ou o usuário atual do aplicativo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ce496-104">You can use these objects to access information that is related to the current application, the computer that the application is installed on, or the current user of the application, respectively.</span></span>  
  
## <a name="myapplication-mycomputer-and-myuser"></a><span data-ttu-id="ce496-105">My. Application, My. Computer e My. User</span><span class="sxs-lookup"><span data-stu-id="ce496-105">My.Application, My.Computer, and My.User</span></span>  
 <span data-ttu-id="ce496-106">Os exemplos a seguir demonstram como informações podem ser recuperadas usando `My`.</span><span class="sxs-lookup"><span data-stu-id="ce496-106">The following examples demonstrate how information can be retrieved using `My`.</span></span>  
  
 <span data-ttu-id="ce496-107">[!code-vb[VbVbcnMy n º&1;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ce496-107">[!code-vb[VbVbcnMy#1](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]</span></span>  
  
 <span data-ttu-id="ce496-108">[!code-vb[VbVbcnMy n º&2;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ce496-108">[!code-vb[VbVbcnMy#2](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_2.vb)]</span></span>  
  
 <span data-ttu-id="ce496-109">Além de recuperar informações, os membros expostos através desses três objetos também permitem que sejam executados métodos relacionados a esse objeto.</span><span class="sxs-lookup"><span data-stu-id="ce496-109">In addition to retrieving information, the members exposed through these three objects also allow you to execute methods related to that object.</span></span> <span data-ttu-id="ce496-110">Por exemplo, você pode acessar uma variedade de métodos para manipular arquivos ou atualizar o registro através de `My.Computer`.</span><span class="sxs-lookup"><span data-stu-id="ce496-110">For instance, you can access a variety of methods to manipulate files or update the registry through `My.Computer`.</span></span>  
  
 <span data-ttu-id="ce496-111">E/s de arquivos é significativamente mais fácil e rápida com `My`, que inclui uma variedade de métodos e propriedades para manipular arquivos, pastas e unidades.</span><span class="sxs-lookup"><span data-stu-id="ce496-111">File I/O is significantly easier and faster with `My`, which includes a variety of methods and properties for manipulating files, directories, and drives.</span></span> <span data-ttu-id="ce496-112">O <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>objeto permite que você ler grandes estruturas de arquivos que têm delimitador ou largura fixa de campos.</xref:Microsoft.VisualBasic.FileIO.TextFieldParser></span><span class="sxs-lookup"><span data-stu-id="ce496-112">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object allows you to read from large structured files that have delimited or fixed-width fields.</span></span> <span data-ttu-id="ce496-113">Este exemplo abre o `TextFieldParser``reader` e o usa para ler de `C:\TestFolder1\test1.txt`.</span><span class="sxs-lookup"><span data-stu-id="ce496-113">This example opens the `TextFieldParser``reader` and uses it to read from `C:\TestFolder1\test1.txt`.</span></span>  
  
 <span data-ttu-id="ce496-114">[!code-vb[VbVbalrTextFieldParser&#23;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ce496-114">[!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_3.vb)]</span></span>  
  
 <span data-ttu-id="ce496-115">`My.Application`permite alterar a cultura do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ce496-115">`My.Application` allows you to change the culture for your application.</span></span> <span data-ttu-id="ce496-116">O exemplo a seguir demonstra como esse método pode ser chamado.</span><span class="sxs-lookup"><span data-stu-id="ce496-116">The following example demonstrates how this method can be called.</span></span>  
  
 <span data-ttu-id="ce496-117">[!code-vb[VbVbcnMy n º&3;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ce496-117">[!code-vb[VbVbcnMy#3](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce496-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce496-118">See Also</span></span>  
 <span data-ttu-id="ce496-119"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span><span class="sxs-lookup"><span data-stu-id="ce496-119"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span></span>   
 <span data-ttu-id="ce496-120"><xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer></span><span class="sxs-lookup"><span data-stu-id="ce496-120"><xref:Microsoft.VisualBasic.Devices.Computer></span></span>   
 <span data-ttu-id="ce496-121"><xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User></span><span class="sxs-lookup"><span data-stu-id="ce496-121"><xref:Microsoft.VisualBasic.ApplicationServices.User></span></span>   
<span data-ttu-id="ce496-122"> [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)</span><span class="sxs-lookup"><span data-stu-id="ce496-122"> [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)</span></span>
