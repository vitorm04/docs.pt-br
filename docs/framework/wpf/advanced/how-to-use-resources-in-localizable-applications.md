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
# <a name="how-to-use-resources-in-localizable-applications"></a>Como: Usar recursos em aplicativos localizáveis
Localização significa adaptar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a diferentes culturas. Para fazer isso, o texto como títulos, legendas, itens de caixa de lista e assim por diante precisam ser traduzido. Para facilitar a tradução, os itens a serem convertidos são coletados em arquivos de recurso. Ver [localizar um aplicativo](how-to-localize-an-application.md) para obter informações sobre como criar um arquivo de recursos para localização. Para fazer um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localizável, os desenvolvedores precisam colocar todos os recursos localizáveis em um assembly de recurso do aplicativo. O assembly de recursos está localizado em diferentes idiomas, e o code-behind usa o gerenciamento de recursos [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] para carregar. Um dos arquivos necessários para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é um arquivo de projeto (. proj). Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto. O exemplo de código a seguir mostra isso.  
  
## <a name="example"></a>Exemplo  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Para usar um recurso em seu aplicativo, você cria uma instância <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar. O exemplo a seguir demonstra como fazer isso.  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
