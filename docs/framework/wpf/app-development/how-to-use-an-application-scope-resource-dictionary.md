---
title: 'Como: Usar um dicionário de recursos no escopo do aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 589e28b3c05496e3fc17055b98240e389faed068
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125367"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="e62ad-102">Como: Usar um dicionário de recursos no escopo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e62ad-102">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="e62ad-103">Este exemplo mostra como definir e usar um dicionário de recursos personalizado de escopo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e62ad-103">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e62ad-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e62ad-104">Example</span></span>  
 <span data-ttu-id="e62ad-105"><xref:System.Windows.Application> expõe um armazenamento de escopo do aplicativo para recursos compartilhados: <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e62ad-105"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e62ad-106">Por padrão, o <xref:System.Windows.Application.Resources%2A> propriedade é inicializada com uma instância das <xref:System.Windows.ResourceDictionary> tipo.</span><span class="sxs-lookup"><span data-stu-id="e62ad-106">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="e62ad-107">Usar essa instância ao obter e definir propriedades de escopo do aplicativo usando <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e62ad-107">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e62ad-108">Para obter mais informações, confira [Como: Obter e definir um recurso de escopo do aplicativo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e62ad-108">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="e62ad-109">Se você tiver vários recursos que você definir usando <xref:System.Windows.Application.Resources%2A>, em vez disso, você pode usar um dicionário de recurso personalizado para armazenar esses recursos e definir <xref:System.Windows.Application.Resources%2A> com ele em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e62ad-109">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="e62ad-110">O exemplo a seguir mostra como declarar um dicionário de recurso personalizado usando XAML.</span><span class="sxs-lookup"><span data-stu-id="e62ad-110">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="e62ad-111">Trocar dicionários de recursos inteiros usando <xref:System.Windows.Application.Resources%2A> permite dar suporte a temas de escopo do aplicativo, onde cada tema é encapsulado por um único dicionário de recursos.</span><span class="sxs-lookup"><span data-stu-id="e62ad-111">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="e62ad-112">O exemplo a seguir mostra como definir o <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="e62ad-112">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="e62ad-113">A seguir mostra como você pode obter os recursos de escopo do aplicativo de dicionário de recursos exposto pelo <xref:System.Windows.Application.Resources%2A> em XAML.</span><span class="sxs-lookup"><span data-stu-id="e62ad-113">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="e62ad-114">O exemplo seguinte mostra como é possível também obter os recursos em código.</span><span class="sxs-lookup"><span data-stu-id="e62ad-114">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="e62ad-115">Há duas considerações a fazer ao usar <xref:System.Windows.Application.Resources%2A>.</span><span class="sxs-lookup"><span data-stu-id="e62ad-115">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="e62ad-116">Primeiro, o dicionário *chave* é um objeto, então você deve usar exatamente a mesma instância de objeto quando ambos definem e obtêm um valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62ad-116">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="e62ad-117">(Note que a chave faz distinção entre maiúsculas e minúsculas ao usar uma cadeia de caracteres.) Segundo, o dicionário *valor* é um objeto, então você precisará converter o valor para o tipo desejado ao obter um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="e62ad-117">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e62ad-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e62ad-118">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="e62ad-119">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="e62ad-119">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="e62ad-120">Dicionários de recursos mesclados</span><span class="sxs-lookup"><span data-stu-id="e62ad-120">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
