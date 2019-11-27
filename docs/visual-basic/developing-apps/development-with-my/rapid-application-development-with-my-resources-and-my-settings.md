---
title: Desenvolvimento de aplicativo rápido com My.Resources e My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349259"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="06c79-102">Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06c79-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="06c79-103">O objeto `My.Resources` fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente os recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06c79-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="06c79-104">Recuperando recursos</span><span class="sxs-lookup"><span data-stu-id="06c79-104">Retrieving Resources</span></span>  

 <span data-ttu-id="06c79-105">Vários recursos, como arquivos de áudio, ícones, imagens e cadeias de caracteres, podem ser recuperados por meio do objeto `My.Resources`.</span><span class="sxs-lookup"><span data-stu-id="06c79-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="06c79-106">Por exemplo, você pode acessar os arquivos de recursos específicos da cultura do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06c79-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="06c79-107">O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenado no arquivo de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06c79-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="06c79-108">O objeto `My.Resources` expõe apenas recursos globais.</span><span class="sxs-lookup"><span data-stu-id="06c79-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="06c79-109">Ele não fornece acesso aos arquivos de recursos associados aos formulários.</span><span class="sxs-lookup"><span data-stu-id="06c79-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="06c79-110">Você deve acessar os recursos do formulário no formulário.</span><span class="sxs-lookup"><span data-stu-id="06c79-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="06c79-111">Da mesma forma, o objeto `My.Settings` fornece acesso às configurações do aplicativo e permite que você armazene e recupere dinamicamente as configurações de propriedade e outras informações para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06c79-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="06c79-112">Para obter mais informações, consulte [My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) Object e [My. Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="06c79-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c79-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06c79-113">See also</span></span>

- [<span data-ttu-id="06c79-114">Objeto My.Resources</span><span class="sxs-lookup"><span data-stu-id="06c79-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="06c79-115">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="06c79-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="06c79-116">Acessando configurações de aplicativo</span><span class="sxs-lookup"><span data-stu-id="06c79-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/index.md)
