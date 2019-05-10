---
title: Globalização do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: bfd901d10fe3158c1c5cb32c3a75f3bc15efd0ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640930"
---
# <a name="globalization-for-wpf"></a>Globalização do WPF
Este tópico apresenta os problemas que você deve estar ciente ao escrever [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos para o mercado global. Os elementos de programação de globalização são definidos no [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] em `System.Globalization`.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalização XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] se baseia [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] e aproveita o suporte de globalização definido no [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] especificação. As seções a seguir descrevem algumas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] recursos que você deve estar atento.

<a name="char_reference"></a>
### <a name="character-references"></a>Referências de Caractere
Uma referência de caractere retorna a unidade de código UTF16 de determinada [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] caractere que representa, em decimal ou hexadecimal. O exemplo a seguir mostra uma referência de caractere decimal do CÓPTICO LETRA maiuscula HORI ou 'Ϩ':

```
&#1000;
```

O exemplo a seguir mostra uma referência de caractere hexadecimal. Observe que ele tem um **x** na frente do número hexadecimal.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Codificando
 A codificação com suporte pelo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] estão [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 e UTF-8. A declaração de codificação é o começo da [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] documento. Se nenhum atributo de codificação existe e não há nenhuma ordem de bytes, o analisador padrão é UTF-8. UTF-8 e UTF-16 são as codificações preferenciais. UTF-7 não tem suporte. O exemplo a seguir demonstra como especificar uma codificação UTF-8 em um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atributo de idioma
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usa [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) para representar o atributo de idioma de um elemento.  Para aproveitar o <xref:System.Globalization.CultureInfo> classe, o valor do atributo de idioma precisa ser um dos nomes de cultura predefinidos por <xref:System.Globalization.CultureInfo>. [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) é herdável na árvore de elementos (pelas regras de XML, não necessariamente devido a herança de propriedade de dependência) e seu valor padrão será uma cadeia de caracteres vazia se ele não for definido explicitamente.

 O atributo de idioma é muito útil para especificar dialetos. Por exemplo, francês tem ortografia, vocabulário e pronúncia diferentes na França, Bélgica, Quebec e Suíça. Também chinês, japonês e coreano compartilham pontos de código no [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], mas as formas ideográficas são diferentes e usam fontes totalmente diferentes.

 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo usa o `fr-CA` atributo de idioma para especificar o francês canadense.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dá suporte a todas [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] recursos, incluindo substitutos. Desde que o conjunto de caracteres pode ser mapeado para [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ele tem suporte. Por exemplo, GB18030 apresenta alguns caracteres que são mapeados para o chinês, japonês e coreano (CFK), extensão A e B e pares substitutos, portanto, ele é totalmente com suporte. Um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo pode usar <xref:System.Globalization.StringInfo> para manipular cadeias de caracteres sem ter noções básicas sobre se eles têm pares substitutos ou combinações de caracteres.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Criando uma Interface do usuário internacional com XAML
 Esta seção descreve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] recursos que você deve considerar ao escrever um aplicativo.

<a name="intl_text"></a>
### <a name="international-text"></a>Texto internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui o processamento interno para sistemas de escrita de todos os Microsoft .NET Framework com suporte.

 Os scripts a seguir tem suporte atualmente:

- Árabe

- Bengali

- Devanágari

- Cirílico

- Grego

- Guzerate

- Gurmukhi

- Hebraico

- Scripts ideográficos

- canarim

- Lao

- Latim

- Malaiala

- Mongol

- Odia

- Siríaco

- Tâmil

- Telugu

- Thaana

- Tailandês*

- Tibetano

 * Nesta versão, a exibição e edição de texto em tailandês tem suporte; quebra de palavras não tem suporte.

 Os scripts a seguir não têm suporte atualmente:

- Khmer

- Hangul antigo coreano

- Myanmar

- Sinhala

 Suporte a mecanismos de sistema de escrita [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fontes. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] fontes podem incluir o [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabelas de layout que permitem que os criadores de fonte projetar fontes tipográficas melhor internacionais e high-end. O [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabelas de layout de fonte contêm informações sobre substituições de glifos, posicionamento de glifo, justificação e posicionamento de linha de base, permitindo que os aplicativos de processamento de texto melhorem o layout de texto.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] fontes permitem a manipulação de glifo de grande conjuntos usando [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] codificação. Tal codificação permite um amplo suporte internacional, bem como para variantes tipográficas de glifos.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderização de texto é alimentada por [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] tecnologia sub-pixel que dá suporte a independência de resolução. Isso significativamente melhora a legibilidade e fornece a capacidade de dar suporte a documentos no estilo de revista de alta qualidade para todos os scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Layout internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece uma forma muito conveniente de dar suporte para layouts horizontais, bidirecionais e verticais. No framework de apresentação o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade pode ser usada para definir o layout. Os padrões de direção de fluxo são:

- *LeftToRight* -layout horizontal para latim, Leste Asiático e assim por diante.

- *RightToLeft* -bidirecional para árabe, hebraico e assim por diante.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Desenvolver aplicativos localizáveis
 Quando você escreve um aplicativo para consumo global, você deve considerar que o aplicativo deve ser localizável. Os tópicos a seguir destacam coisas a se considerar.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interface do Usuário Multilíngue
 Interfaces de usuário multilíngue (MUI) é um [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] suporte para a alternância [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de um idioma para outro. Um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo usa o modelo de assembly para oferecer suporte ao MUI. Um aplicativo contém assemblies de com neutralidade de idioma, bem como assemblies satélite dependentes de idioma em recursos. O ponto de entrada é .EXE gerenciado no assembly principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] carregador de recursos aproveita o [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]do Gerenciador de recursos para dar suporte ao recurso de pesquisa e fallback. Vários assemblies satélite funcionam com o mesmo assembly principal. O assembly de recurso que é carregado depende o <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> do thread atual.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interface do usuário localizável
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos usam [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para definir suas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permite que os desenvolvedores especifiquem uma hierarquia de objetos com um conjunto de propriedades e lógica. O principal uso de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é desenvolver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos, mas ele pode ser usado para especificar uma hierarquia de qualquer [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objetos. A maioria dos desenvolvedores usam [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para especificar seu aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] e usar uma linguagem de programação como c# para reagir a interação do usuário.

 Do ponto de vista do recurso, uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo projetado para descrever um dependente de idioma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é um elemento de recurso e, portanto, o formato final de distribuição deve ser localizável para oferecer suporte a idiomas internacionais. Porque [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não pode tratar eventos, muitos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplicativos contêm blocos de código para fazer isso. Para obter mais informações, consulte [visão geral de XAML (WPF)](xaml-overview-wpf.md). Código é retirado e compilado em binários diferentes quando um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo é indexado no formato BAML de XAML. O formulário BAML de arquivos XAML, imagens e outros tipos de objetos de recursos gerenciados são inseridos no assembly de recursos satélite, que pode ser localizado em outros idiomas ou o assembly principal quando a localização não é necessária.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos dão suporte a todos os [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] recursos, incluindo tabelas de cadeia de caracteres, imagens e assim por diante.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Construindo aplicativos localizáveis
 Localização significa adaptar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a diferentes culturas. Para fazer um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localizável, os desenvolvedores precisam colocar todos os recursos localizáveis em um assembly de recurso do aplicativo. O assembly de recursos está localizado em diferentes idiomas, e o code-behind usa o gerenciamento de recursos [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] para carregar. Um dos arquivos necessários para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é um arquivo de projeto (. proj). Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto. O exemplo de um arquivo. csproj a seguir mostra como fazer isso.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Para usar um recurso em seu aplicativo instancie um <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar. O exemplo a seguir demonstra como fazer isso.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Usando o ClickOnce com aplicativos localizados
 O ClickOnce é uma nova tecnologia de implantação do Windows Forms que acompanhará o Visual Studio 2005. Ele permite a instalação do aplicativo e a atualização de aplicativos da Web. Quando um aplicativo que foi implantado com o ClickOnce é localizado, ele somente pode ser exibido na cultura localizada. Por exemplo, se um aplicativo implantado está localizado para japonês ele só pode ser exibido em japonês [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] não no Windows em inglês. Isso apresenta um problema porque ele é um cenário comum para os usuários japoneses executarem uma versão em inglês do Windows.

 A solução para esse problema é configurar o atributo de fallback de idioma neutro. Um desenvolvedor de aplicativos pode, opcionalmente, remover recursos do assembly principal e especificar que os recursos podem ser encontrados em um assembly satélite correspondente a uma cultura específica. Para controlar esse processo use a <xref:System.Resources.NeutralResourcesLanguageAttribute>. O construtor do <xref:System.Resources.NeutralResourcesLanguageAttribute> classe tem duas assinaturas, uma que usa um <xref:System.Resources.UltimateResourceFallbackLocation> parâmetro para especificar o local onde o <xref:System.Resources.ResourceManager> deve extrair os recursos de fallback: assembly principal ou assembly satélite. O exemplo a seguir mostra como usar o atributo. Para o local de fallback final, o código faz com que o <xref:System.Resources.ResourceManager> para procurar os recursos no subdiretório "de" do diretório do assembly em execução.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Consulte também

- [Visão geral de globalização e localização do WPF](wpf-globalization-and-localization-overview.md)
