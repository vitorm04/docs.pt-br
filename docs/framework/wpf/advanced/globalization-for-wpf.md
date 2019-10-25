---
title: Globalização do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 7826bbfca09cce7508d7352c647bafae93504e58
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395836"
---
# <a name="globalization-for-wpf"></a>Globalização do WPF
Este tópico apresenta problemas que você deve estar atento ao escrever aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] para o mercado global. Os elementos de programação de globalização são definidos no .NET no namespace <xref:System.Globalization>.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalização XAML
 Extensible Application Markup Language (XAML) baseia-se em [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] e aproveita o suporte à globalização definido na especificação [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. As seções a seguir descrevem alguns recursos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dos quais você deve estar atento.

<a name="char_reference"></a>
### <a name="character-references"></a>Referências de Caractere
Uma referência de caractere fornece a unidade de código UTF16 do caractere Unicode específico que ela representa, em decimal ou hexadecimal. O exemplo a seguir mostra uma referência de caractere decimal para a letra maiúscula CÓPTICA HORI ou ' Ϩ ':

```
&#1000;
```

O exemplo a seguir mostra uma referência de caractere hexadecimal. Observe que ele tem um **x** na frente do número hexadecimal.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Codificando
 A codificação com suporte de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é ASCII, Unicode UTF-16 e UTF-8. A instrução Encoding está no início do documento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Se nenhum atributo de codificação existe e não há nenhuma ordem de bytes, o analisador padrão é UTF-8. UTF-8 e UTF-16 são as codificações preferenciais. UTF-7 não tem suporte. O exemplo a seguir demonstra como especificar uma codificação UTF-8 em um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atributo de idioma
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usa [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) para representar o atributo language de um elemento.  Para aproveitar a classe <xref:System.Globalization.CultureInfo>, o valor do atributo language precisa ser um dos nomes de cultura predefinidos por <xref:System.Globalization.CultureInfo>. [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) é herdável na árvore de elementos (pelas regras de XML, não necessariamente devido a herança de propriedade de dependência) e seu valor padrão será uma cadeia de caracteres vazia se ele não for definido explicitamente.

 O atributo de idioma é muito útil para especificar dialetos. Por exemplo, francês tem ortografia, vocabulário e pronúncia diferentes na França, Bélgica, Quebec e Suíça. Além disso, o chinês, o japonês e o coreano compartilham pontos de código em Unicode, mas as formas ideográficas são diferentes e usam fontes totalmente diferentes.

 O exemplo a seguir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] usa o atributo de linguagem `fr-CA` para especificar o francês canadense.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dá suporte a todos os recursos Unicode, incluindo substitutos. Desde que o conjunto de caracteres possa ser mapeado para Unicode, ele tem suporte. Por exemplo, GB18030 apresenta alguns caracteres que são mapeados para o chinês, japonês e coreano (CFK), extensão A e B e pares substitutos, portanto, ele é totalmente com suporte. Um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode usar <xref:System.Globalization.StringInfo> para manipular cadeias de caracteres sem entender se eles têm pares substitutos ou combinando.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Criando uma Interface do usuário internacional com XAML
 Esta seção descreve os recursos [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que você deve considerar ao escrever um aplicativo.

<a name="intl_text"></a>
### <a name="international-text"></a>Texto internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui o processamento interno para todos os sistemas de escrita com suporte do Microsoft .NET Framework.

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

- Oriá

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

 Todos os mecanismos do sistema de escrita dão suporte a fontes OpenType. As fontes OpenType podem incluir as tabelas de layout OpenType que permitem aos criadores de fontes criar melhores fontes tipográficas internacionais e de ponta. As tabelas de layout de fonte OpenType contêm informações sobre substituições de glifos, posicionamento de glifo, justificação e posicionamento de linha de base, permitindo que aplicativos de processamento de texto aprimorem o layout de texto.

 As fontes OpenType permitem a manipulação de grandes conjuntos de glifos usando a codificação Unicode. Tal codificação permite um amplo suporte internacional, bem como para variantes tipográficas de glifos.

 a renderização de texto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é alimentada pela tecnologia de subpixel do Microsoft ClearType que dá suporte à independência de resolução. Isso significativamente melhora a legibilidade e fornece a capacidade de dar suporte a documentos no estilo de revista de alta qualidade para todos os scripts.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Layout internacional
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece uma forma muito conveniente de dar suporte para layouts horizontais, bidirecionais e verticais. No Framework de apresentação, a propriedade <xref:System.Windows.FrameworkElement.FlowDirection%2A> pode ser usada para definir o layout. Os padrões de direção de fluxo são:

- *LeftToRight* -layout horizontal para latim, Leste Asiático e assim por diante.

- *RightToLeft* -bidirecional para árabe, hebraico e assim por diante.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Desenvolver aplicativos localizáveis
 Quando você escreve um aplicativo para consumo global, você deve considerar que o aplicativo deve ser localizável. Os tópicos a seguir destacam coisas a se considerar.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Interface do Usuário Multilíngue
 MUI (Multilingual User Interfaces) é um suporte da Microsoft para alternar interfaces de usuário de um idioma para outro. Um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa o modelo de assembly para dar suporte ao MUI. Um aplicativo contém assemblies de com neutralidade de idioma, bem como assemblies satélite dependentes de idioma em recursos. O ponto de entrada é .EXE gerenciado no assembly principal.  o carregador de recursos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aproveita o Gerenciador de recursos de [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] para dar suporte à pesquisa e ao fallback de recursos. Vários assemblies satélite funcionam com o mesmo assembly principal. O assembly de recurso que é carregado depende do <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> do thread atual.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interface do usuário localizável
 os aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usam [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para definir seus [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permite que os desenvolvedores especifiquem uma hierarquia de objetos com um conjunto de propriedades e lógica. O uso principal de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é desenvolver aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mas pode ser usado para especificar uma hierarquia de objetos Common Language Runtime (CLR). A maioria dos desenvolvedores usa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para especificar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do seu aplicativo e usar uma linguagem C# de programação, como reagir à interação do usuário.

 De um ponto de vista de recurso, um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] criado para descrever um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dependente de idioma é um elemento de recurso e, portanto, seu formato de distribuição final deve ser localizável para dar suporte a idiomas internacionais. Como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não pode manipular eventos, muitos aplicativos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] contêm blocos de código para fazer isso. Para obter mais informações, consulte [visão geral de XAML (WPF)](xaml-overview-wpf.md). O código é removido e compilado em binários diferentes quando um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é indexado na forma BAML do XAML. O formulário BAML de arquivos XAML, imagens e outros tipos de objetos de recursos gerenciados são inseridos no assembly de recursos satélite, que pode ser localizado em outros idiomas ou o assembly principal quando a localização não é necessária.

> [!NOTE]
> os aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dão suporte a todos os recursos de @no__t 1CLR, incluindo tabelas de cadeias de caracteres, imagens e assim por diante.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Construindo aplicativos localizáveis
 Localização significa adaptar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a diferentes culturas. Para tornar um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localizável, os desenvolvedores precisam criar todos os recursos localizáveis em um assembly de recurso. O assembly de recursos é localizado em idiomas diferentes, e o code-behind usa a API de gerenciamento de recursos para carregar. Um dos arquivos necessários para um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é um arquivo de projeto (. proj). Todos os recursos que você usa em seu aplicativo devem ser incluídos no arquivo de projeto. O exemplo de um arquivo. csproj a seguir mostra como fazer isso.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Para usar um recurso em seu aplicativo, instancie um <xref:System.Resources.ResourceManager> e carregue o recurso que você deseja usar. O exemplo a seguir demonstra como fazer isso.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Usando o ClickOnce com aplicativos localizados
 O ClickOnce é uma nova tecnologia de implantação Windows Forms que será fornecida com o Visual Studio 2005. Ele permite a instalação do aplicativo e a atualização de aplicativos da Web. Quando um aplicativo que foi implantado com o ClickOnce é localizado, ele somente pode ser exibido na cultura localizada. Por exemplo, se um aplicativo implantado for localizado para japonês, ele só poderá ser exibido em Japonês [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] não no Windows em inglês. Isso apresenta um problema porque é um cenário comum para os usuários japoneses executarem uma versão em inglês do Windows.

 A solução para esse problema é configurar o atributo de fallback de idioma neutro. Um desenvolvedor de aplicativos pode, opcionalmente, remover recursos do assembly principal e especificar que os recursos podem ser encontrados em um assembly satélite correspondente a uma cultura específica. Para controlar esse processo, use o <xref:System.Resources.NeutralResourcesLanguageAttribute>. O construtor da classe <xref:System.Resources.NeutralResourcesLanguageAttribute> tem duas assinaturas, uma que usa um parâmetro <xref:System.Resources.UltimateResourceFallbackLocation> para especificar o local em que o <xref:System.Resources.ResourceManager> deve extrair os recursos de fallback: assembly principal ou assembly satélite. O exemplo a seguir mostra como usar o atributo. Para o local de fallback final, o código faz com que o <xref:System.Resources.ResourceManager> procure os recursos no subdiretório "de" do diretório do assembly em execução no momento.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Consulte também

- [Visão geral de globalização e localização do WPF](wpf-globalization-and-localization-overview.md)
