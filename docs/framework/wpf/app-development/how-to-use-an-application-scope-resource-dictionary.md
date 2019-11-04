---
title: Como usar um dicionário de recursos de escopo do aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 5bfb3ed0304598a5acf4b7682bf4a4169c5153d1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459803"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="70d82-102">Como usar um dicionário de recursos de escopo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="70d82-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="70d82-103">Este exemplo mostra como definir e usar um dicionário de recursos personalizado de escopo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70d82-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70d82-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70d82-104">Example</span></span>  
 <span data-ttu-id="70d82-105">o <xref:System.Windows.Application> expõe um repositório de escopo de aplicativo para recursos compartilhados: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="70d82-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="70d82-106">Por padrão, a propriedade <xref:System.Windows.Application.Resources%2A> é inicializada com uma instância do tipo <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="70d82-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="70d82-107">Você usa essa instância quando Obtém e define as propriedades de escopo do aplicativo usando <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="70d82-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="70d82-108">Para obter mais informações, consulte [como: obter e definir um recurso de escopo de aplicativo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="70d82-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="70d82-109">Se você tiver vários recursos que você definiu usando <xref:System.Windows.Application.Resources%2A>, poderá usar um dicionário de recursos personalizados para armazenar esses recursos e definir <xref:System.Windows.Application.Resources%2A> com ele.</span><span class="sxs-lookup"><span data-stu-id="70d82-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="70d82-110">O seguinte mostra como você declara um dicionário de recursos personalizados usando XAML.</span><span class="sxs-lookup"><span data-stu-id="70d82-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="70d82-111">A troca de dicionários de recursos inteiros usando o <xref:System.Windows.Application.Resources%2A> permite que você ofereça suporte a temas de escopo de aplicativo, onde cada tema é encapsulado por um único dicionário de recursos.</span><span class="sxs-lookup"><span data-stu-id="70d82-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="70d82-112">O exemplo a seguir mostra como definir o <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="70d82-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="70d82-113">O seguinte mostra como você pode obter recursos de escopo de aplicativo do dicionário de recursos exposto por <xref:System.Windows.Application.Resources%2A> em XAML.</span><span class="sxs-lookup"><span data-stu-id="70d82-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="70d82-114">O exemplo seguinte mostra como é possível também obter os recursos em código.</span><span class="sxs-lookup"><span data-stu-id="70d82-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="70d82-115">Há duas considerações a serem feitas ao usar <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="70d82-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="70d82-116">Primeiro, a *chave* de dicionário é um objeto, portanto, você deve usar exatamente a mesma instância de objeto quando ambas estiverem Configurando e obtendo um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="70d82-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="70d82-117">(Observe que a chave diferencia maiúsculas de minúsculas ao usar uma cadeia de caracteres.) Em segundo lugar, o *valor* Dictionary é um objeto, portanto, você precisará converter o valor para o tipo desejado ao obter um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="70d82-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d82-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70d82-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="70d82-119">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="70d82-119">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="70d82-120">Dicionários de recursos mesclados</span><span class="sxs-lookup"><span data-stu-id="70d82-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
