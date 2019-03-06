---
title: 'Como: Usar recursos em aplicativos localizáveis'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376150"
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="f91ca-102">Como: Usar recursos em aplicativos localizáveis</span><span class="sxs-lookup"><span data-stu-id="f91ca-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="f91ca-103">Localização significa adaptar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a diferentes culturas.</span><span class="sxs-lookup"><span data-stu-id="f91ca-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="f91ca-104">Para fazer isso, o texto como títulos, legendas, itens de caixa de lista e assim por diante precisam ser traduzido.</span><span class="sxs-lookup"><span data-stu-id="f91ca-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="f91ca-105">Para facilitar a tradução, os itens a serem convertidos são coletados em arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="f91ca-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="f91ca-106">Ver [localizar um aplicativo](how-to-localize-an-application.md) para obter informações sobre como criar um arquivo de recursos para localização.</span><span class="sxs-lookup"><span data-stu-id="f91ca-106">See [Localize an Application](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="f91ca-107">Para fazer um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localizável, os desenvolvedores precisam colocar todos os recursos localizáveis em um assembly de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f91ca-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="f91ca-108">O assembly de recursos está localizado em diferentes idiomas, e o code-behind usa o gerenciamento de recursos [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] para carregar.</span><span class="sxs-lookup"><span data-stu-id="f91ca-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="f91ca-109">Um dos arquivos necessários para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é um arquivo de projeto (. proj).</span><span class="sxs-lookup"><span data-stu-id="f91ca-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="f91ca-110">Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f91ca-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="f91ca-111">O exemplo de código a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="f91ca-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f91ca-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f91ca-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="f91ca-113">Para usar um recurso em seu aplicativo, você cria uma instância <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="f91ca-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="f91ca-114">O exemplo a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f91ca-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
