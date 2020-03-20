---
title: Empacotando fontes com aplicativos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187083"
---
# <a name="packaging-fonts-with-applications"></a>Empacotando fontes com aplicativos
Este tópico fornece uma visão geral de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] como empacotar fontes com seu aplicativo.  
  
> [!NOTE]
> Assim como a maioria dos tipos de software, as fontes são licenciadas, ao invés de vendidas. As licenças que regem o uso de fontes variam de fornecedor para fornecedor, mas, em geral, a maioria das licenças, incluindo aquelas que cobrem as fontes que a Microsoft fornece com aplicativos e Windows, não permitem que as fontes sejam incorporadas dentro de aplicativos ou redistribuídas de outra forma. Portanto, como desenvolvedor, é sua responsabilidade assegurar que você tenha os direitos de licença necessários de qualquer fonte que você inserir em um aplicativo ou redistribuir.  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>Introdução a empacotamento de fontes  
 Você pode facilmente empacotar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fontes como recursos dentro de seus aplicativos para exibir texto de interface do usuário e outros tipos de conteúdo baseado em texto. As fontes podem ser separadas ou inseridas nos arquivos de assembly do aplicativo. Você também pode criar uma biblioteca de fontes somente recursos, que seu aplicativo pode fazer referência.  
  
 As fontes OpenType e TrueType® contêm um tipo de sinalizador, fsType, que indica os direitos de licenciamento da fonte. No entanto, esse sinalizador de tipo somente referencia fontes embutidas armazenadas em um documento. Ele não referencia fontes incorporadas em um aplicativo. Você pode recuperar os direitos de incorporação <xref:System.Windows.Media.GlyphTypeface> de fonte para <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> uma fonte criando um objeto e fazendo referência à sua propriedade. Consulte a seção "OS/2 e Windows Metrics" da [Especificação OpenType](https://www.microsoft.com/typography/otspec/os2.htm) para obter mais informações sobre o sinalizador fsType.  
  
 O site [da Microsoft Typography](https://docs.microsoft.com/typography/) inclui informações de contato que podem ajudá-lo a localizar um determinado fornecedor de fontes ou encontrar um fornecedor de fontes para trabalho personalizado.  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a>Adicionando fontes como itens de conteúdo  
 Você pode adicionar fontes ao seu aplicativo como itens de conteúdo de projeto que são separados dos arquivos de assembly do aplicativo. Isso significa que os itens de conteúdo não são inseridos como recursos em um assembly. O seguinte exemplo de arquivo de projeto mostra como definir itens de conteúdo.  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 Para garantir que o aplicativo possa usar as fontes em tempo de execução, as fontes devem ser acessíveis no diretório de implantação do aplicativo. O `<CopyToOutputDirectory>` elemento no arquivo de projeto do aplicativo permite copiar automaticamente as fontes para o diretório de implantação do aplicativo durante o processo de compilação. O seguinte exemplo de arquivo de projeto mostra como copiar fontes para o diretório de implantação.  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 O exemplo de código a seguir mostra como referenciar a fonte do aplicativo como um item de conteúdo. O item de conteúdo referenciado deve estar no mesmo diretório que os arquivos de assembly do aplicativo.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a>Adicionando fontes como itens de recurso  
 Você pode adicionar fontes ao seu aplicativo como itens de recurso de projeto que são inseridos nos arquivos de assembly do aplicativo. Usar um subdiretório separado para recursos ajuda a organizar arquivos de projeto do aplicativo. O seguinte exemplo de arquivo de projeto mostra como definir fontes como itens de recursos em um subdiretório separado.  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
> Quando você adicionar fontes como recursos ao seu aplicativo, certifique-se de que você está definindo o `<Resource>` elemento, e não o `<EmbeddedResource>` elemento no arquivo de projeto do aplicativo. O `<EmbeddedResource>` elemento para a ação de construção não é suportado.  
  
 O exemplo de marcação a seguir mostra como referenciar os recursos de fonte do aplicativo.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>Referenciando itens de recurso de fonte do código  
 Para referenciar itens de recurso de fonte a partir do código, você deve fornecer uma referência de recurso de fonte de duas partes: o identificador de recursos uniforme base (URI); e a referência de localização da fonte. Esses valores são utilizados <xref:System.Windows.Media.FontFamily.%23ctor%2A> como parâmetros para o método. O exemplo de código a seguir mostra como referenciar os `resources`recursos de fonte do aplicativo no subdiretório de projeto chamado .  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 O uri (font uniform resource identifier, identificador de recursos uniforme base) pode incluir o subdiretório de aplicativo onde o recurso de fonte reside. Neste caso, a referência de localização da fonte não precisaria especificar um`./`diretório, mas teria que incluir um líder " ", que indica que o recurso de fonte está no mesmo diretório especificado pelo identificador de recursos de uniforme base (URI). O exemplo de código a seguir mostra uma maneira alternativa de referenciar o item de recurso de fonte. Ele é equivalente ao exemplo de código anterior.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>Referenciando fontes do mesmo subdiretório do aplicativo  
 Você pode colocar ambos os arquivos de conteúdo e recursos de aplicativo dentro do mesmo subdiretório definido pelo usuário do seu projeto de aplicativo. O seguinte exemplo de arquivo de projeto mostra uma página de conteúdo e recursos de fonte definidos no mesmo subdiretório.  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Como o conteúdo do aplicativo e a fonte estão no mesmo subdiretório, a referência da fonte é relativa ao conteúdo do aplicativo. Os exemplos a seguir mostram como referenciar o recurso de fonte do aplicativo quando a fonte está no mesmo diretório do aplicativo.  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>Enumerando fontes em um aplicativo  
 Para enumerar fontes como itens de recurso em <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> seu <xref:System.Windows.Media.Fonts.GetTypefaces%2A> aplicativo, use o método ou ou o método. O exemplo a seguir <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> mostra como usar <xref:System.Windows.Media.FontFamily> o método para retornar a coleção de objetos do local da fonte do aplicativo. Nesse caso, o aplicativo contém um subdiretório chamado "recursos".  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 O exemplo a seguir <xref:System.Windows.Media.Fonts.GetTypefaces%2A> mostra como usar <xref:System.Windows.Media.Typeface> o método para retornar a coleção de objetos do local da fonte do aplicativo. Nesse caso, o aplicativo contém um subdiretório chamado "recursos".  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a>Criando uma biblioteca de recursos de fonte  
 Você pode criar uma biblioteca somente recursos que contém apenas fontes. Nenhum código faz parte desse tipo de projeto de biblioteca. Criar uma biblioteca somente recursos é uma técnica comum para desacoplar recursos do código do aplicativo que os utiliza. Isso também permite que o assembly de biblioteca seja incluído em vários projetos de aplicativo. O seguinte exemplo de arquivo de projeto mostra as partes principais de um projeto de biblioteca somente recursos.  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a>Referenciando uma fonte em uma biblioteca de recursos  
 Para referenciar uma fonte em uma biblioteca de recursos de seu aplicativo, você deve prefixar a referência da fonte com o nome do assembly de biblioteca. Nesse caso, o assembly de recursos de fonte é "FontLibrary". Para separar o nome do assembly de referência dentro do assembly, use um caractere ';'. Adicionar a palavra-chave "Component" seguida da referência ao nome da fonte completa a referência completa ao recurso da biblioteca de fontes. O exemplo de código a seguir mostra como referenciar uma fonte em um assembly de biblioteca de recursos.  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> Este SDK contém um conjunto de fontes OpenType [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de exemplo que você pode usar com aplicativos. As fontes são definidas em uma biblioteca somente recursos. Para obter mais informações, consulte [Sample OpenType Font Pack](sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>Limitações no uso de fontes  
 A lista a seguir descreve várias limitações na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] embalagem e uso de fontes em aplicativos:  
  
- **Bits de permissão de incorporação de fontes:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos não verificam ou impõem bits de permissão de incorporação de fonte. Consulte a seção [Introduction_to_Packing Fontes](#introduction_to_packaging_fonts) para obter mais informações.  
  
- **Site de fontes de origem:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos não permitem uma referência de fonte a um identificador de recursos uniforme http ou ftp (URI).  
  
- **URI absoluto usando o pacote: notação:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos <xref:System.Windows.Media.FontFamily> não permitem que você crie um objeto programáticamente usando "pack:" como parte da referência do identificador de recursos uniforme absoluto (URI) a uma fonte. Por exemplo, `"pack://application:,,,/resources/#Pericles Light"` é uma referência de fonte inválida.  
  
- **Incorporação de fonte automática:** no tempo de design, não há suporte para pesquisar o uso de um aplicativo de fontes e incorporar automaticamente as fontes nos recursos do aplicativo.  
  
- **Subconjuntos de fontes:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os aplicativos não dão suporte à criação de subconjuntos de fontes para documentos não fixos.  
  
- Em casos em que há uma referência incorreta, o aplicativo volta a usar uma fonte disponível.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Typography: links, notícias e contatos](https://docs.microsoft.com/typography/)
- [Especificação OpenType](https://www.microsoft.com/typography/otspec/)
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Pacote de fontes OpenType de amostra](sample-opentype-font-pack.md)
