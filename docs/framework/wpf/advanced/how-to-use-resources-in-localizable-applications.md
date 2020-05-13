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
# <a name="how-to-use-resources-in-localizable-apps"></a>Como: usar recursos em aplicativos localizáveis

Localização significa adaptar uma interface do usuário a diferentes culturas. Para fazer isso, um texto como títulos, legendas e itens da caixa de listagem devem ser traduzidos. Para facilitar a tradução, os itens a serem convertidos são coletados em arquivos de recursos. Consulte [localizar um aplicativo](how-to-localize-an-application.md) para obter informações sobre como criar um arquivo de recurso para localização. Para tornar um aplicativo do WPF localizável, os desenvolvedores precisam criar todos os recursos localizáveis em um assembly de recurso. O assembly de recursos é localizado em idiomas diferentes, e o code-behind usa a API de gerenciamento de recursos para carregar.

## <a name="example"></a>Exemplo

Um dos arquivos necessários para um aplicativo do WPF é um arquivo de projeto (. proj). Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto. O exemplo de XAML a seguir mostra isso.

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

Para usar um recurso em seu aplicativo, crie uma instância <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar. O código C# a seguir demonstra como fazer isso.

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a>Confira também

- [Localizar um aplicativo](how-to-localize-an-application.md)
