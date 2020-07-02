---
title: Como usar um dicionário de recursos de escopo do aplicativo
description: Saiba como definir e usar um dicionário de recursos personalizados de escopo de aplicativo no Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 9d117dea6c554339b4b462b9bf37b80da2dc477f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613703"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a><span data-ttu-id="7b7fe-103">Como usar um dicionário de recursos de escopo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="7b7fe-103">How to: Use an Application-Scope Resource Dictionary</span></span>
<span data-ttu-id="7b7fe-104">Este exemplo mostra como definir e usar um dicionário de recursos personalizado de escopo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-104">This example shows how to define and use an application-scope custom resource dictionary.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b7fe-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b7fe-105">Example</span></span>  
 <span data-ttu-id="7b7fe-106"><xref:System.Windows.Application>expõe um repositório de escopo de aplicativo para recursos compartilhados: <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="7b7fe-106"><xref:System.Windows.Application> exposes an application-scope store for shared resources: <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="7b7fe-107">Por padrão, a <xref:System.Windows.Application.Resources%2A> propriedade é inicializada com uma instância do <xref:System.Windows.ResourceDictionary> tipo.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-107">By default, the <xref:System.Windows.Application.Resources%2A> property is initialized with an instance of the <xref:System.Windows.ResourceDictionary> type.</span></span> <span data-ttu-id="7b7fe-108">Você usa essa instância quando Obtém e define as propriedades de escopo de aplicativo usando <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="7b7fe-108">You use this instance when you get and set application-scope properties using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="7b7fe-109">Para obter mais informações, consulte [como: obter e definir um recurso de escopo de aplicativo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7b7fe-109">For more information, see [How to: Get and Set an Application-Scope Resource](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348547(v=vs.100)).</span></span>
  
 <span data-ttu-id="7b7fe-110">Se você tiver vários recursos que você definiu usando <xref:System.Windows.Application.Resources%2A> , poderá usar um dicionário de recursos personalizados para armazenar esses recursos e defini <xref:System.Windows.Application.Resources%2A> -los com ele.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-110">If you have multiple resources that you set using <xref:System.Windows.Application.Resources%2A>, you can instead use a custom resource dictionary to store those resources and set <xref:System.Windows.Application.Resources%2A> with it instead.</span></span> <span data-ttu-id="7b7fe-111">O seguinte mostra como você declara um dicionário de recursos personalizados usando XAML.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-111">The following shows how you declare a custom resource dictionary using XAML.</span></span>
  
 [!code-xaml[HOWTOResourceDictionaries#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <span data-ttu-id="7b7fe-112">A troca de dicionários de recursos inteiros usando <xref:System.Windows.Application.Resources%2A> permite que você dê suporte a temas de escopo de aplicativo, em que cada tema é encapsulado por um único dicionário de recursos.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-112">Swapping entire resource dictionaries using <xref:System.Windows.Application.Resources%2A> allows you to support application-scope themes, where each theme is encapsulated by a single resource dictionary.</span></span> <span data-ttu-id="7b7fe-113">O exemplo a seguir mostra como definir o <xref:System.Windows.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="7b7fe-113">The following example shows how to set the <xref:System.Windows.ResourceDictionary>.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 <span data-ttu-id="7b7fe-114">O seguinte mostra como você pode obter recursos de escopo de aplicativo do dicionário de recursos exposto pelo <xref:System.Windows.Application.Resources%2A> em XAML.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-114">The following shows how you can get application-scope resources from the resource dictionary exposed by <xref:System.Windows.Application.Resources%2A> in XAML.</span></span>  
  
 [!code-xaml[HOWTOResourceDictionaries#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 <span data-ttu-id="7b7fe-115">O exemplo seguinte mostra como é possível também obter os recursos em código.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-115">The following shows how you can also get the resources in code.</span></span>  
  
 [!code-csharp[HOWTOResourceDictionaries#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <span data-ttu-id="7b7fe-116">Há duas considerações a serem feitas ao usar o <xref:System.Windows.Application.Resources%2A> .</span><span class="sxs-lookup"><span data-stu-id="7b7fe-116">There are two considerations to make when using <xref:System.Windows.Application.Resources%2A>.</span></span> <span data-ttu-id="7b7fe-117">Primeiro, a *chave* de dicionário é um objeto, portanto, você deve usar exatamente a mesma instância de objeto quando ambas estiverem Configurando e obtendo um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-117">First, the dictionary *key* is an object, so you must use exactly the same object instance when both setting and getting a property value.</span></span> <span data-ttu-id="7b7fe-118">(Observe que a chave diferencia maiúsculas de minúsculas ao usar uma cadeia de caracteres.) Em segundo lugar, o *valor* Dictionary é um objeto, portanto, você precisará converter o valor para o tipo desejado ao obter um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b7fe-118">(Note that the key is case-sensitive when using a string.) Second, the dictionary *value* is an object, so you will have to convert the value to the desired type when getting a property value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7fe-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b7fe-119">See also</span></span>

- <xref:System.Windows.ResourceDictionary>
- <xref:System.Windows.Application.Resources%2A>
- [<span data-ttu-id="7b7fe-120">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="7b7fe-120">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="7b7fe-121">Dicionários de recursos mesclados</span><span class="sxs-lookup"><span data-stu-id="7b7fe-121">Merged Resource Dictionaries</span></span>](../advanced/merged-resource-dictionaries.md)
