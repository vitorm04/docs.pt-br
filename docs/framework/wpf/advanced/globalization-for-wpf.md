---
title: Globalização do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: fd99d97d677ef588c3f7e2a178190377d72c74ce
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400631"
---
# <a name="globalization-for-wpf"></a>Globalização do WPF
Este tópico apresenta problemas que você deve estar atento ao escrever [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos para o mercado global. Os elementos de programação de globalização [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] são `System.Globalization`definidos no no.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalização XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]baseia-se [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] no e aproveita o suporte à globalização definido [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] na especificação. As seções a seguir descrevem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] alguns recursos dos quais você deve estar ciente.

<a name="char_reference"></a>
### <a name="character-references"></a>Referências de Caractere
Uma referência de caractere fornece a unidade de código UTF16 do [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] caractere específico que ela representa, em decimal ou hexadecimal. O exemplo a seguir mostra uma referência de caractere decimal para a letra maiúscula CÓPTICA HORI ou ' Ϩ ':

```
&#1000;
```

O exemplo a seguir mostra uma referência de caractere hexadecimal. Observe que ele tem um **x** na frente do número hexadecimal.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Codificando
 A codificação com suporte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é ASCII, [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 e UTF-8. A instrução Encoding está no início do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] documento. Se nenhum atributo de codificação existe e não há nenhuma ordem de bytes, o analisador padrão é UTF-8. UTF-8 e UTF-16 são as codificações preferenciais. UTF-7 não tem suporte. O exemplo a seguir demonstra como especificar uma codificação UTF-8 em um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atributo de idioma
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]usa [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) para representar o atributo language de um elemento.  Para aproveitar a <xref:System.Globalization.CultureInfo> classe, o valor do atributo language precisa ser um dos nomes de cultura predefinidos pelo <xref:System.Globalization.CultureInfo>. [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) é herdável na árvore de elementos (pelas regras de XML, não necessariamente devido a herança de propriedade de dependência) e seu valor padrão será uma cadeia de caracteres vazia se ele não for definido explicitamente.

 O atributo de idioma é muito útil para especificar dialetos. Por exemplo, francês tem ortografia, vocabulário e pronúncia diferentes na França, Bélgica, Quebec e Suíça. Além disso, o idioma chinês, japonês e coreano compartilham [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]pontos de código no, mas as formas ideográficas são diferentes e usam fontes totalmente diferentes.

 O exemplo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a seguir usa `fr-CA` o atributo language para especificar o francês canadense.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dá suporte [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] a todos os recursos, incluindo substitutos. Contanto que o conjunto de caracteres possa ser mapeado [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]para, ele tem suporte. Por exemplo, GB18030 apresenta alguns caracteres que são mapeados para o chinês, japonês e coreano (CFK), extensão A e B e pares substitutos, portanto, ele é totalmente com suporte. Um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo pode usar <xref:System.Globalization.StringInfo> para manipular cadeias de caracteres sem entender se eles têm pares substitutos ou caractere de combinação.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Criando uma Interface do usuário internacional com XAML
 Esta seção descreve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] os recursos que você deve considerar ao escrever um aplicativo.

<a name="intl_text"></a>
### <a name="international-text"></a>Texto internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]inclui o processamento interno para todos os Microsoft .NET Framework com suporte para sistemas de gravação.

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

 \* Nesta versão, a exibição e edição de texto em tailandês tem suporte; quebra de palavras não tem suporte.

 Os scripts a seguir não têm suporte atualmente:

- Khmer

- Hangul antigo coreano

- Myanmar

- Sinhala

 Todos os mecanismos do sistema de [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] escrita dão suporte a fontes. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]as fontes podem incluir [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] as tabelas de layout que permitem que os criadores de fontes projetem melhores fontes tipográficas internacionais e de ponta. As [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabelas de layout de fonte contêm informações sobre substituições de glifos, posicionamento de glifo, justificação e posicionamento de linha de base, permitindo que aplicativos de processamento de texto aprimorem o layout de texto.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]as fontes permitem a manipulação de grandes conjuntos de [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] glifos usando codificação. Tal codificação permite um amplo suporte internacional, bem como para variantes tipográficas de glifos.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a renderização de texto é [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] alimentada por uma tecnologia de subpixel que dá suporte à independência de resolução. Isso significativamente melhora a legibilidade e fornece a capacidade de dar suporte a documentos no estilo de revista de alta qualidade para todos os scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Layout internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece uma forma muito conveniente de dar suporte para layouts horizontais, bidirecionais e verticais. Na estrutura de apresentação <xref:System.Windows.FrameworkElement.FlowDirection%2A> , a propriedade pode ser usada para definir o layout. Os padrões de direção de fluxo são:

- *LeftToRight* -layout horizontal para latim, Leste Asiático e assim por diante.

- *RightToLeft* -bidirecional para árabe, hebraico e assim por diante.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Desenvolver aplicativos localizáveis
 Quando você escreve um aplicativo para consumo global, você deve considerar que o aplicativo deve ser localizável. Os tópicos a seguir destacam coisas a se considerar.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interface do Usuário Multilíngue
 MUI (Multilingual User Interfaces) é um [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] suporte para alternar [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de um idioma para outro. Um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo usa o modelo de assembly para dar suporte ao mui. Um aplicativo contém assemblies de com neutralidade de idioma, bem como assemblies satélite dependentes de idioma em recursos. O ponto de entrada é .EXE gerenciado no assembly principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]o carregador de recursos aproveita o [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]Gerenciador de recursos do para dar suporte à pesquisa e ao fallback de recursos. Vários assemblies satélite funcionam com o mesmo assembly principal. O assembly de recurso que é carregado depende <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> do do thread atual.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interface do usuário localizável
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]os aplicativos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam para definir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]seus. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permite que os desenvolvedores especifiquem uma hierarquia de objetos com um conjunto de propriedades e lógica. O principal uso do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é desenvolver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos, mas pode ser usado para especificar uma hierarquia de qualquer objeto Common Language Runtime (CLR). A maioria dos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] desenvolvedores usa o para especificar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] seus aplicativos e usar uma linguagem de C# programação, como para reagir à interação do usuário.

 Do ponto de vista de um recurso, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo criado para descrever um dependente [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de idioma é um elemento de recurso e, portanto, seu formato de distribuição final deve ser localizável para dar suporte a idiomas internacionais. Como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] o não pode manipular [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] eventos, muitos aplicativos contêm blocos de código para fazer isso. Para obter mais informações, consulte [visão geral de XAML (WPF)](xaml-overview-wpf.md). O código é removido e compilado em binários diferentes quando um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo é indexado na forma BAML do XAML. O formulário BAML de arquivos XAML, imagens e outros tipos de objetos de recursos gerenciados são inseridos no assembly de recursos satélite, que pode ser localizado em outros idiomas ou o assembly principal quando a localização não é necessária.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]os aplicativos dão suporte [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]a todos os recursos do CLR, incluindo tabelas de cadeias de caracteres, imagens e assim por diante.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Construindo aplicativos localizáveis
 Localização significa adaptar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a diferentes culturas. Para tornar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo localizável, os desenvolvedores precisam criar todos os recursos localizáveis em um assembly de recurso. O assembly de recursos é localizado em idiomas diferentes, e o code-behind usa a API de gerenciamento de recursos para carregar. Um dos arquivos necessários para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo é um arquivo de projeto (. proj). Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto. O exemplo de um arquivo. csproj a seguir mostra como fazer isso.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Para usar um recurso em seu aplicativo, instancie <xref:System.Resources.ResourceManager> a e carregue o recurso que você deseja usar. O exemplo a seguir demonstra como fazer isso.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Usando o ClickOnce com aplicativos localizados
 O ClickOnce é uma nova tecnologia de implantação Windows Forms que será fornecida com o Visual Studio 2005. Ele permite a instalação do aplicativo e a atualização de aplicativos da Web. Quando um aplicativo que foi implantado com o ClickOnce é localizado, ele somente pode ser exibido na cultura localizada. Por exemplo, se um aplicativo implantado for localizado para japonês, ele só poderá ser [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] exibido em Japonês e não em janelas em inglês. Isso apresenta um problema porque é um cenário comum para os usuários japoneses executarem uma versão em inglês do Windows.

 A solução para esse problema é configurar o atributo de fallback de idioma neutro. Um desenvolvedor de aplicativos pode, opcionalmente, remover recursos do assembly principal e especificar que os recursos podem ser encontrados em um assembly satélite correspondente a uma cultura específica. Para controlar esse processo, use <xref:System.Resources.NeutralResourcesLanguageAttribute>o. O construtor da <xref:System.Resources.NeutralResourcesLanguageAttribute> classe tem duas assinaturas, uma que usa um <xref:System.Resources.UltimateResourceFallbackLocation> parâmetro para especificar o local em que o <xref:System.Resources.ResourceManager> deve extrair os recursos de fallback: assembly principal ou assembly satélite. O exemplo a seguir mostra como usar o atributo. Para o local de fallback final, o código faz <xref:System.Resources.ResourceManager> com que o procure os recursos no subdiretório "de" do diretório do assembly em execução no momento.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Consulte também

- [Visão geral de globalização e localização do WPF](wpf-globalization-and-localization-overview.md)
