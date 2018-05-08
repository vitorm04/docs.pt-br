---
title: Como usar recursos em aplicativos localizáveis
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 82a24feb4008b6cfd7c1751c6449c0d8515ffe87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Como usar recursos em aplicativos localizáveis
Localização significa adaptar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a diferentes culturas. Para fazer isso, texto como títulos, legendas, itens de caixa de lista e assim por diante precisam ser convertido. Para facilitar a conversão de itens a serem traduzidos são coletados em arquivos de recursos. Consulte [localizar um aplicativo](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) para obter informações sobre como criar um arquivo de recursos para localização. Para fazer um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localizável, os desenvolvedores precisam colocar todos os recursos localizáveis em um conjunto de recursos do aplicativo. O conjunto de recursos é localizado em diferentes idiomas e do code-behind usa o gerenciamento de recursos [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] para carregar. Um dos arquivos necessários para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é um arquivo de projeto (. proj). Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto. O exemplo de código a seguir mostra isso.  
  
## <a name="example"></a>Exemplo  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Para usar um recurso em seu aplicativo, você cria uma instância <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar. O exemplo a seguir demonstra como fazer isso.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
