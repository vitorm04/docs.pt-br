---
title: Como usar recursos em aplicativos localizáveis
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212469"
---
# <a name="how-to-use-resources-in-localizable-apps"></a><span data-ttu-id="42b26-102">Como: usar recursos em aplicativos localizáveis</span><span class="sxs-lookup"><span data-stu-id="42b26-102">How to: Use resources in localizable apps</span></span>

<span data-ttu-id="42b26-103">Localização significa adaptar uma interface do usuário a diferentes culturas.</span><span class="sxs-lookup"><span data-stu-id="42b26-103">Localization means to adapt a user interface to different cultures.</span></span> <span data-ttu-id="42b26-104">Para fazer isso, um texto como títulos, legendas e itens da caixa de listagem devem ser traduzidos.</span><span class="sxs-lookup"><span data-stu-id="42b26-104">To do this, text such as titles, captions, and list box items must be translated.</span></span> <span data-ttu-id="42b26-105">Para facilitar a tradução, os itens a serem convertidos são coletados em arquivos de recursos.</span><span class="sxs-lookup"><span data-stu-id="42b26-105">To make translation easier, the items to be translated are collected into resource files.</span></span> <span data-ttu-id="42b26-106">Consulte [localizar um aplicativo](how-to-localize-an-application.md) para obter informações sobre como criar um arquivo de recurso para localização.</span><span class="sxs-lookup"><span data-stu-id="42b26-106">See [Localize an app](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="42b26-107">Para tornar um aplicativo do WPF localizável, os desenvolvedores precisam criar todos os recursos localizáveis em um assembly de recurso.</span><span class="sxs-lookup"><span data-stu-id="42b26-107">To make a WPF application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="42b26-108">O assembly de recursos é localizado em idiomas diferentes, e o code-behind usa a API de gerenciamento de recursos para carregar.</span><span class="sxs-lookup"><span data-stu-id="42b26-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span>

## <a name="example"></a><span data-ttu-id="42b26-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42b26-109">Example</span></span>

<span data-ttu-id="42b26-110">Um dos arquivos necessários para um aplicativo do WPF é um arquivo de projeto (. proj).</span><span class="sxs-lookup"><span data-stu-id="42b26-110">One of the files required for a WPF application is a project file (.proj).</span></span> <span data-ttu-id="42b26-111">Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="42b26-111">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="42b26-112">O exemplo de XAML a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="42b26-112">The following XAML example shows this.</span></span>

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

<span data-ttu-id="42b26-113">Para usar um recurso em seu aplicativo, crie uma instância <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="42b26-113">To use a resource in your application, instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="42b26-114">O código C# a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="42b26-114">The following C# code demonstrates how to do this.</span></span>

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a><span data-ttu-id="42b26-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="42b26-115">See also</span></span>

- [<span data-ttu-id="42b26-116">Localizar um aplicativo</span><span class="sxs-lookup"><span data-stu-id="42b26-116">Localize an app</span></span>](how-to-localize-an-application.md)
