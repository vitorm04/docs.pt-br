---
title: Personalizando projetos e estendendo My com o Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
ms.openlocfilehash: 97933a9d014a54d5b6e333090cddccace99fcc3c
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960938"
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="b32cc-102">Personalizando projetos e estendendo My com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b32cc-102">Customizing Projects and Extending My with Visual Basic</span></span>

<span data-ttu-id="b32cc-103">Você pode personalizar modelos de projeto para fornecer objetos `My` adicionais.</span><span class="sxs-lookup"><span data-stu-id="b32cc-103">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="b32cc-104">Isso facilita para outros desenvolvedores a localização e o uso de seus objetos.</span><span class="sxs-lookup"><span data-stu-id="b32cc-104">This makes it easy for other developers to find and use your objects.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b32cc-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b32cc-105">In this section</span></span>

- [<span data-ttu-id="b32cc-106">Estendendo o Meu Namespace em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b32cc-106">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)  
 <span data-ttu-id="b32cc-107">Descreve como adicionar membros e valores personalizados ao namespace `My` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b32cc-107">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>
- [<span data-ttu-id="b32cc-108">Empacotando e implantando minhas extensões personalizadas</span><span class="sxs-lookup"><span data-stu-id="b32cc-108">Packaging and Deploying Custom My Extensions</span></span>](packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="b32cc-109">Descreve como publicar extensões de namespace de `My` personalizadas usando modelos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b32cc-109">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>
- [<span data-ttu-id="b32cc-110">Estendendo o modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b32cc-110">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="b32cc-111">Descreve como especificar suas próprias extensões para o modelo de aplicativo, substituindo membros da classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.</span><span class="sxs-lookup"><span data-stu-id="b32cc-111">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>
- [<span data-ttu-id="b32cc-112">Personalizando quais objetos estão disponíveis em My</span><span class="sxs-lookup"><span data-stu-id="b32cc-112">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="b32cc-113">Descreve como controlar quais `My` objetos são habilitados definindo a constante de compilação condicional de \_do seu projeto com MyType.</span><span class="sxs-lookup"><span data-stu-id="b32cc-113">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b32cc-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b32cc-114">Related sections</span></span>

- [<span data-ttu-id="b32cc-115">Desenvolvimento com My</span><span class="sxs-lookup"><span data-stu-id="b32cc-115">Development with My</span></span>](../development-with-my/index.md)  
 <span data-ttu-id="b32cc-116">Descreve quais objetos de `My` estão disponíveis em diferentes tipos de projeto por padrão.</span><span class="sxs-lookup"><span data-stu-id="b32cc-116">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="b32cc-117">Visão geral do modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b32cc-117">Overview of the Visual Basic Application Model</span></span>](../development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="b32cc-118">Descreve o modelo de Visual Basic para controlar o comportamento de aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b32cc-118">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>
- [<span data-ttu-id="b32cc-119">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="b32cc-119">How My Depends on Project Type</span></span>](../development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="b32cc-120">Descreve quais objetos de `My` estão disponíveis em diferentes tipos de projeto por padrão.</span><span class="sxs-lookup"><span data-stu-id="b32cc-120">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="b32cc-121">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="b32cc-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="b32cc-122">Discute como o compilador usa a compilação condicional para selecionar seções específicas de código para compilar e excluir outras seções.</span><span class="sxs-lookup"><span data-stu-id="b32cc-122">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="b32cc-123">Descreve o objeto `My` que fornece propriedades, métodos e eventos relacionados ao aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="b32cc-123">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>

## <a name="see-also"></a><span data-ttu-id="b32cc-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b32cc-124">See also</span></span>

- [<span data-ttu-id="b32cc-125">Desenvolvendo aplicativos com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b32cc-125">Developing Applications with Visual Basic</span></span>](../index.md)
