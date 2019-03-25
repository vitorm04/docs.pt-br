---
title: URIs "pack://" no WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: e84f586e621aa54d7e8a8f62e605ec3016cfb757
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411272"
---
# <a name="pack-uris-in-wpf"></a>URIs "pack://" no WPF
No Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] são usados para identificar e carregar arquivos de várias maneiras, incluindo o seguinte:  
  
-   Especificando o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para mostrar quando um aplicativo é iniciado.  
  
-   Carregar imagens.  
  
-   Navegar até as páginas.  
  
-   Carregar arquivos de dados não executáveis.  
  
 Além disso, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pode ser usado para identificar e carregar arquivos de uma variedade de locais, incluindo o seguinte:  
  
-   O assembly atual.  
  
-   Um assembly referenciado.  
  
-   Um local relativo a um assembly.  
  
-   O site de origem do aplicativo.  
  
 Para fornecer um mecanismo consistente para identificar e carregar esses tipos de arquivos a partir desses locais, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] utiliza a extensibilidade a *esquema de URI de pacote*. Este tópico fornece uma visão geral do esquema, aborda como construir um pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para uma variedade de cenários, aborda absolute e relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] e [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolução, antes de mostrar como usar o pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] de ambos os marcação e o código.  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>O esquema de URI de pacote  
 O pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema é usado pelas [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) especificação (OPC), que descreve um modelo para organizar e identificar conteúdo. Os principais elementos desse modelo são pacotes e partes, onde um *pacote* é um contêiner lógico para uma ou mais lógica *partes*. A imagem a seguir ilustra esse conceito.  
  
 ![Diagrama de pacote e partes](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)  
  
 Para identificar partes, a especificação OPC utiliza a extensibilidade RFC 2396 (identificadores de recurso uniforme (URI): Sintaxe genérica) para definir o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema.  
  
 O esquema especificado por um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é definido por seu prefixo; http, ftp e file são exemplos bem conhecidos. O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema usa "pack" como seu esquema e contém dois componentes: autoridade e caminho. Este é o formato para um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 pack://*authority*/*path*
  
 O *autoridade* Especifica o tipo de pacote que contém a parte, enquanto o *caminho* Especifica o local de uma parte dentro de um pacote.  
  
 Esse conceito é ilustrado pela figura a seguir:  
  
 ![Relação entre pacote, autoridade e caminho](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)  
  
 Os pacotes e peças são análogos a aplicativos e arquivos, pois um aplicativo (pacote) pode incluir um ou mais arquivos (peças), incluindo:  
  
-   Arquivos de recursos que são compilados no assembly local.  
  
-   Arquivos de recursos que são compilados em um assembly referenciado.  
  
-   Arquivos de recursos que são compilados em um assembly de referência.  
  
-   Arquivos de conteúdo.  
  
-   Arquivos de site de origem.  
  
 Para acessar esses tipos de arquivos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dá suporte a duas autoridades: application: Application:/// e siteoforigin:///: / / /. A autoridade application:/// identifica arquivos de dados de aplicativo que são conhecidos no tempo de compilação, incluindo arquivos de recurso e conteúdo. A autoridade siteoforigin:/// identifica arquivos de site de origem. O escopo de cada autoridade é mostrado na figura a seguir.  
  
 ![Diagrama URI de pacote](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)  
  
> [!NOTE]
>  O componente de autoridade de um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é inserida [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que aponta para um pacote e deve estar em conformidade com RFC 2396. Além disso, o caractere “/” deve ser substituído pelo caractere “,”; caracteres reservados como “%” e “?” devem ser ignorados. Para ver os detalhes, consulte o OPC.  
  
 As seções a seguir explicam como construir um pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] usando essas duas autoridades em conjunto com os caminhos adequados para a identificação de recurso, conteúdo e site de arquivos de origem.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>URIs de pacote de arquivo de recurso  
 Arquivos de recurso são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` itens e são compilados em assemblies. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dá suporte à construção de pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que pode ser usado para identificar arquivos de recursos que são compilados no assembly local ou compilados em um assembly que é referenciado no assembly local.  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>Arquivo de recurso de assembly local  
 O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um recurso de arquivo é compilado no assembly local utiliza a autoridade e caminho a seguir:  
  
-   **Autoridade**: application:///.  
  
-   **Caminho**: O nome do arquivo de recurso, incluindo seu caminho, relativo à pasta raiz do projeto do assembly local.  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta do projeto do assembly local.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta de projeto do assembly local.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>Arquivo de recurso de assembly referenciado  
 O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um recurso de arquivo é compilado em um assembly referenciado utiliza a autoridade e caminho a seguir:  
  
-   **Autoridade**: application:///.  
  
-   **Caminho**: O nome de um arquivo de recurso que é compilado em um assembly referenciado. O caminho deve estar de acordo com o seguinte formato:  
  
     *AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*  
  
    -   **AssemblyShortName**: o nome curto do assembly referenciado.  
  
    -   **;Version** [opcional]: a versão do assembly referenciado que contém o arquivo de recurso. É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.  
  
    -   **;PublicKey** [opcional]: a chave pública que foi usada para assinar o assembly referenciado. É usada quando são carregados dois ou mais assemblies referenciados com o mesmo nome curto.  
  
    -   **;component**: especifica que o assembly referenciado é referenciado a partir do assembly local.  
  
    -   **/Path**: o nome do arquivo de recurso, incluindo o caminho, em relação à raiz da pasta de projeto do assembly referenciado.  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na raiz da pasta do projeto do assembly referenciado.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado em uma subpasta da pasta de projeto do assembly referenciado.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de recurso que está localizado na pasta raiz da pasta de projeto de uma versão específica do assembly referenciado.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Observe que o pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] sintaxe para arquivos de recurso de assembly referenciado pode ser usada apenas com o aplicativo: autoridade. Por exemplo, o seguinte não é suportado em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>URIs de pacote de arquivo de conteúdo  
 O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de conteúdo usa a autoridade e caminho a seguir:  
  
-   **Autoridade**: application:///.  
  
-   **Caminho**: O nome do arquivo de conteúdo, incluindo seu caminho relativo ao local de sistema do arquivo do assembly executável principal do aplicativo.  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado na mesma pasta do assembly executável.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo de conteúdo, localizado em uma subpasta que é relativo ao assembly executável do aplicativo.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  Não é possível acessar os arquivos de conteúdo do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]. O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquema dá suporte apenas a navegação para [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] arquivos que estão localizados no site de origem.  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>URIs de pacote de site de origem  
 O pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um site de origem arquivo utiliza a autoridade e caminho a seguir:  
  
-   **Autoridade**: siteoforigin:///.  
  
-   **Caminho**: O nome do site do arquivo de origem, incluindo seu caminho relativo ao local do qual o assembly executável foi iniciado.  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site de origem, armazenado no local do qual o assembly executável é iniciado.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 O exemplo a seguir mostra o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site de origem, armazenado na subpasta é relativo ao local do qual o assembly executável do aplicativo é iniciado.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>Arquivos de paginação  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos que são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens são compilados em assemblies da mesma forma como arquivos de recurso. Consequentemente, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens podem ser identificados usando o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para arquivos de recurso.  
  
 Os tipos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos que normalmente são configurados como [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` itens têm um dos seguintes como seu elemento raiz:  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>Absolutos vs. URIs de pacote relativo  
 Um pacote totalmente qualificado [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] inclui o esquema, a autoridade e o caminho, e ele é considerado um pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Como simplificação para os desenvolvedores, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos normalmente permitem que você defina atributos adequados com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], que inclui apenas o caminho.  
  
 Por exemplo, considere a possibilidade de pacote absoluto a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para um arquivo de recurso no assembly local.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 O pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que se refere a esse recurso de arquivo seria o seguinte.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Porque o site de arquivos de origem não estão associados a assemblies, eles só podem ser referenciados para com o pacote absoluto [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  
  
 Por padrão, um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é considerado relativo ao local da marcação ou código que contém a referência. Se uma barra invertida inicial for usada, no entanto, o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] referência, em seguida, é considerada relativa à raiz do aplicativo. Considere, por exemplo, a estrutura de projeto a seguir.  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Se o Page1.xaml contém um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que referencia *raiz*\SubFolder\Page2.xaml, a referência pode usar o pacote relativo a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `Page2.xaml`  
  
 Se o Page1.xaml contém um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que referencia *raiz*\Page2.xaml, a referência pode usar o pacote relativo a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>Resolução de URI de pacote  
 O formato de pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] torna possível para o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para diferentes tipos de arquivos tenham a mesma aparência. Por exemplo, considere a possibilidade de pacote absoluto a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Este pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pode se referir a um arquivo de recurso no assembly local ou um arquivo de conteúdo. O mesmo é verdadeiro para relativo a seguir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
 `/ResourceOrContentFile.xaml`  
  
 Para determinar o tipo de arquivo que um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] se refere, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolve [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para arquivos de recursos em assemblies locais e arquivos de conteúdo usando a heurística a seguir:  
  
1.  Teste os metadados de assembly para um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo que corresponde ao pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
2.  Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo for encontrado, o caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refere-se a um arquivo de conteúdo.  
  
3.  Se o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo não for encontrado, verificar o conjunto de arquivos de recursos que é compilados no assembly local.  
  
4.  Se um arquivo de recurso que corresponde ao caminho do pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for encontrado, o caminho do pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refere-se a um arquivo de recurso.  
  
5.  Se o recurso não for encontrado, criado internamente <xref:System.Uri> é inválido.  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolução não se aplica a [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que se referem ao seguinte:  
  
-   Arquivos de conteúdo em assemblies referenciados: não há suporte para esses tipos de arquivo por [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Arquivos inseridos em assemblies referenciados: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que os identificam são exclusivos, porque eles incluem o nome do assembly referenciado e o `;component` sufixo.  
  
-   Site de arquivos de origem: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que os identificam são exclusivos, porque eles são os únicos arquivos que podem ser identificados pelo pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que contêm o siteoforigin:///: autoridade.  
  
 Uma simplificação que pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] permite a resolução é para código um pouco independente dos locais dos arquivos de recurso e conteúdo. Por exemplo, se você tiver um arquivo de recurso no assembly local que foi reconfigurado para ser um arquivo de conteúdo, o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o recurso permanece o mesmo, assim como o código que usa o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>Programando com URIs de pacote  
 Muitas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implementam propriedades que podem ser definidas com o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], incluindo:  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 Essas propriedades podem ser definidas a partir de marcação e código. Esta seção demonstra as construções básicas para ambos e, depois, mostra exemplos de cenários comuns.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>Utilizando URIs de pacote em marcação  
 Um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é especificado na marcação, definindo o elemento de um atributo com o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Por exemplo:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Tabela 1 mostra o pacote absoluto a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar na marcação.  
  
 Tabela 1: URIs de pacote absolutos em marcação  
  
|Arquivo|Pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Arquivo de recurso - assembly local|`"pack://application:,,,/ResourceFile.xaml"`|  
|Arquivo de recurso em subpasta - assembly local|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Arquivo de recurso - assembly referenciado|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Arquivo de recurso em subpasta de assembly referenciado|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Arquivo de recurso em assembly referenciado com controle de versão|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|Arquivo de conteúdo|`"pack://application:,,,/ContentFile.xaml"`|  
|Arquivo de conteúdo em subpasta|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Arquivo de site de origem|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Arquivo de site de origem em subpasta|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Tabela 2 mostra o pacote relativo a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar na marcação.  
  
 Tabela 2: URIs de pacote relativos em marcação  
  
|Arquivo|Pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Arquivo de recurso em assembly local|`"/ResourceFile.xaml"`|  
|Arquivo de recurso em subpasta de assembly local|`"/Subfolder/ResourceFile.xaml"`|  
|Arquivo de recurso em assembly referenciado|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Arquivo de recurso em subpasta de assembly referenciado|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Arquivo de conteúdo|`"/ContentFile.xaml"`|  
|Arquivo de conteúdo em subpasta|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>Utilizando URIs de pacote em código  
 Especifique um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] no código pela instanciação do <xref:System.Uri> classe e passando o pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] como um parâmetro para o construtor. Isso é demonstrado no exemplo a seguir.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Por padrão, o <xref:System.Uri> classe considera pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para serem absolutos. Consequentemente, uma exceção é gerada quando uma instância das <xref:System.Uri> classe é criada com um pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Felizmente, o <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> sobrecarga da <xref:System.Uri> construtor de classe aceita um parâmetro do tipo <xref:System.UriKind> para permitir que você especifique se um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é relativo ou absoluto.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 Você deve especificar apenas <xref:System.UriKind.Absolute> ou <xref:System.UriKind.Relative> quando você tiver certeza de que o pacote fornecido [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] é um ou outro. Se você não souber o tipo de pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que é usada, como quando um usuário insere um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] em tempo de execução, use <xref:System.UriKind.RelativeOrAbsolute> em vez disso.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Tabela 3 ilustra um pacote relativo a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabela 3: URIs de pacote absolutos em código  
  
|Arquivo|Pacote absoluto [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Arquivo de recurso - assembly local|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Arquivo de recurso em subpasta - assembly local|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Arquivo de recurso - assembly referenciado|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Arquivo de recurso em subpasta de assembly referenciado|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Arquivo de recurso em assembly referenciado com controle de versão|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Arquivo de conteúdo|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|Arquivo de conteúdo em subpasta|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Arquivo de site de origem|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Arquivo de site de origem em subpasta|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Tabela 4 mostra um pacote relativo a vários [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] que você pode especificar no código usando <xref:System.Uri?displayProperty=nameWithType>.  
  
 Tabela 4: URIs de pacote relativos em código  
  
|Arquivo|Pacote relativo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|Arquivo de recurso - assembly local|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Arquivo de recurso em subpasta - assembly local|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Arquivo de recurso - assembly referenciado|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Arquivo de recurso em subpasta - assembly referenciado|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Arquivo de conteúdo|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|Arquivo de conteúdo em subpasta|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>Cenários comuns de URI de pacote  
 As seções anteriores discutiram como construir um pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] para identificar o recurso, conteúdo e site de arquivos de origem. No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], essas construções são usadas em uma variedade de formas e as seções a seguir abrangem vários usos comuns.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>Especificando a interface do usuário para mostrar quando um aplicativo foi iniciado  
 <xref:System.Windows.Application.StartupUri%2A> Especifica o primeiro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para mostrar quando um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo é iniciado. Para aplicativos autônomos, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pode ser uma janela, conforme mostrado no exemplo a seguir.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Aplicativos autônomos e [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] também pode especificar uma página como a interface do usuário inicial, conforme mostrado no exemplo a seguir.  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Se o aplicativo é um aplicativo autônomo e uma página é especificada com <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] abre uma <xref:System.Windows.Navigation.NavigationWindow> para hospedar a página. Para [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], a página é exibida no navegador host.  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>Navegando até uma página  
 O exemplo a seguir mostra como navegar até uma página.  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Para obter mais informações sobre as várias maneiras de navegar no [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [visão geral da navegação](navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>Especificando um ícone de janela  
 O exemplo a seguir mostra como usar um URI para especificar um ícone de janela.  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Para obter mais informações, consulte <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>Carregando arquivos de imagem, áudio e vídeo  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite que aplicativos usem uma grande variedade de tipos de mídia, que podem ser identificados e carregados com o pacote de [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], conforme mostrado nos exemplos a seguir.  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Para obter mais informações sobre como trabalhar com conteúdo de mídia, consulte [gráficos e multimídia](../graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>Carregando um dicionário de recursos a partir do site de origem  
 Dicionários de recursos (<xref:System.Windows.ResourceDictionary>) pode ser usado para dar suporte a temas do aplicativo. Uma maneira de criar e gerenciar temas é criando diferentes temas como dicionários de recursos localizados em um site de origem do aplicativo. Isso permite que temas sejam adicionados e atualizados sem recompilar e reimplantar um aplicativo. Esses dicionários de recursos podem ser identificados e carregados usando [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], que é mostrado no exemplo a seguir.  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Para uma visão geral de temas [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consulte [Styling and Templating](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Consulte também
- [Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF](wpf-application-resource-content-and-data-files.md)
