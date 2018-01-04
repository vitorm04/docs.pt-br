---
title: "Visão geral de globalização e localização do WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f2bc9021ca376b7b27f74efed6866a907b480ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-globalization-and-localization-overview"></a>Visão geral de globalização e localização do WPF
Quando você limita a disponibilidade de seu produto a apenas um idioma, você limita sua base de clientes potenciais a uma fração da população mundial de 6,5 bilhões. Se desejar que seus aplicativos alcancem um público global, a localização econômica de seu produto será uma das melhores e mais econômicas maneiras de alcançar mais clientes.  
  
 Esta visão geral apresenta globalização e localização na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. A globalização é o design e o desenvolvimento de aplicativos que são executados em várias localizações. Por exemplo, a globalização dá suporte a interfaces do usuário localizadas e a dados regionais para usuários em culturas diferentes. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornece recursos globalizados de design, incluindo o layout automático, assemblies satélite e atributos localizados e comentários.
  
 A localização é a tradução de recursos do aplicativo em versões localizadas para culturas específicas às quais o aplicativo dá suporte. Quando você localiza no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você usa as APIs no <xref:System.Windows.Markup.Localizer> namespace. Energia essas APIs a [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016) ferramenta de linha de comando. Para obter informações sobre como criar e usar LocBaml, consulte [localizar um aplicativo](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Melhores práticas de globalização e localização no WPF  
 Você pode aproveitar ao máximo a funcionalidade de globalização e localização incorporado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seguindo o design de interface do usuário e dicas relacionadas a localização que esta seção fornece.  
  
### <a name="best-practices-for-wpf-ui-design"></a>Melhores práticas de design de interface do usuário no WPF  
 Quando você cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– com base em [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], considere a implementação dessas práticas recomendadas:  
  
-   Gravar seu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; evite criar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] no código. Quando você cria sua [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], expô-lo por meio de APIs de localização interno.  
  
-   Evite usar posições absolutas e tamanhos fixos para dispor conteúdo; em vez disso, use dimensionamento relativo ou automático.
  
    -   Use <xref:System.Windows.Window.SizeToContent%2A>; e mantenha as larguras e alturas definidas como `Auto`.  
  
    -   Evite usar <xref:System.Windows.Controls.Canvas> para dispor [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.  
  
    -   Use <xref:System.Windows.Controls.Grid> e seu recurso de compartilhamento de tamanho.  
  
-   Forneça espaço extra nas margens, pois, de modo geral, o texto localizado exige mais espaço. O espaço extra permite possíveis caracteres estendidos.  
  
-   Habilitar <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> em <xref:System.Windows.Controls.TextBlock> para evitar recorte.
  
-   Definir o **XML: lang** atributo. Esse atributo descreve a cultura de um elemento específico e seus elementos filho. O valor dessa propriedade altera o comportamento de vários recursos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Por exemplo, ele altera o comportamento de hifenização, verificação ortográfica, substituição de números, formatação de scripts complexos e fallback de fontes. Consulte [globalização para WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md) para obter mais informações sobre como configurar o [XML: lang em XAML de tratamento](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md).  
  
-   Crie uma fonte composta personalizada para obter um melhor controle de fontes que são usadas para diferentes idiomas. Por padrão, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa a fonte GlobalUserInterface na pasta Windows\Fonts.  
  
-   Quando você cria aplicativos de navegação que podem ser localizados em uma cultura que apresenta texto em um formato da direita para esquerda, defina explicitamente o <xref:System.Windows.FlowDirection> de cada página para garantir que a página não herda <xref:System.Windows.FlowDirection> do <xref:System.Windows.Navigation.NavigationWindow>.  
  
-   Quando você cria aplicativos autônomos de navegação que são hospedados fora de um navegador, defina o <xref:System.Windows.Application.StartupUri%2A> para seu aplicativo inicial para um <xref:System.Windows.Navigation.NavigationWindow> em vez da uma página (por exemplo, `<Application StartupUri="NavigationWindow.xaml">`). Esse design permite que você altere o <xref:System.Windows.FlowDirection> da janela e a barra de navegação. Para obter mais informações e um exemplo, consulte [Globalization Homepage Sample](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
### <a name="best-practices-for-wpf-localization"></a>Melhores práticas de localização no WPF  
 Quando você localiza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplicativos, considere a implementação dessas práticas recomendadas:  
  
-   Use comentários de localização para fornecer contexto extra para localizadores.  
  
-   Use atributos de localização para controlar a localização em vez de seletivamente omitir <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades nos elementos. Consulte [atributos de localização e comentários](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md) para obter mais informações.  
  
-   Use **msbuild /t: updateuid** e **checkuid** para adicionar e verificar <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades no seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Use <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades para controlar alterações entre o desenvolvimento e a localização. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>propriedades ajudam você a localizar novas alterações de desenvolvimento. Se você adicionar manualmente <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades para um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], a tarefa é normalmente tediosa e menos precisa.  
  
    -   Edite ou altere <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades depois de iniciar a localização.  
  
    -   Não use duplicata <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades (Lembre-se essa dica quando você usar o comando copiar e colar).  
  
    -   Definir o `UltimateResourceFallback` local AssemblyInfo para especificar o idioma apropriado para retorno (por exemplo, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).  
  
         Se você decidir incluir o idioma de origem no assembly principal, omitindo o `<UICulture>` marca no arquivo de projeto, defina o `UltimateResourceFallback` local do assembly principal, em vez do satélite (por exemplo, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>Localizar um aplicativo WPF  
 Quando você localiza um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo, você tem várias opções. Por exemplo, você pode vincular os recursos localizáveis em seu aplicativo para um [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] de arquivo, armazenar texto localizável em tabelas resx ou fazer com que o localizador use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivos. Esta seção descreve um fluxo de trabalho de localização que usa o formato BAML de XAML, que oferece vários benefícios:  
  
-   É possível localizar após o build.  
  
-   É possível atualizar para uma versão mais nova do formato BAML de XAML com localizações de uma versão mais antiga do formato BAML de XAML, para que você possa localizar simultaneamente com o desenvolvimento.  
  
-   Você pode validar elementos de origem original e a semântica em tempo de compilação porque o formulário BAML do XAML é a forma compilada de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
### <a name="localization-build-process"></a>Processo de build para localização  
 Ao desenvolver um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo, o processo de compilação para a localização é o seguinte:  
  
-   O desenvolvedor cria e globaliza o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativo. No arquivo de projeto o desenvolvedor define `<UICulture>en-US</UICulture>` para que quando o aplicativo é compilado, um assembly principal com neutralidade de idioma é gerado. Esse assembly tem um arquivo satélite .resources.dll que contém todos os recursos localizáveis. Opcionalmente, você pode manter o idioma de origem no assembly principal porque nossa localização [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] suporta a extração do assembly principal.  
  
-   Quando o arquivo é compilado, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é convertido para o formulário BAML do XAML. Culturalmente neutro `MyDialog.exe` e culturalmente dependentes (em inglês) `MyDialog.resources.dll` arquivos são liberados para o cliente de língua inglesa.  
  
### <a name="localization-workflow"></a>Fluxo de trabalho de localização  
 O processo de localização começa depois que o não localizado `MyDialog.resources.dll` arquivo é criado. O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos e propriedades no original [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são extraídas do formulário de BAML do XAML em pares chave-valor usando o [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] em <xref:System.Windows.Markup.Localizer>. Os localizadores usam os pares chave-valor para localizar o aplicativo. É possível gerar um novo .resource.dll com base nos novos valores após a conclusão da localização.  
  
 As chaves de pares chave-valor são `x:Uid` valores que são colocados pelo desenvolvedor no original [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Essas `x:Uid` valores permitem que o [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] para rastrear e mesclar as alterações que ocorrem entre o desenvolvedor e o localizador durante a localização. Por exemplo, se o desenvolvedor altera o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] após o localizador ter começado a localização, você pode mesclar a alteração de desenvolvimento com o trabalho já concluído de localização para que o trabalho de conversão mínimo é perdido.  
  
 O gráfico a seguir mostra um fluxo de trabalho típico de localização que se baseia no formato BAML de XAML. Este diagrama supõe que o desenvolvedor grava o aplicativo em inglês. O desenvolvedor cria e globaliza o aplicativo do WPF. No arquivo de projeto o desenvolvedor define `<UICulture>en-US</UICulture>` para que na compilação, um assembly principal neutro de idioma é gerado com um. Resources contendo todos os recursos localizáveis. Como alternativa, é possível manter o idioma de origem no assembly principal, pois as APIs de localização do WPF dão suporte à extração do assembly principal. Após o processo de build, o XAML é compilado para o BAML. O MyDialog.exe.resources.dll com neutralidade de cultura é enviado para o cliente falante de inglês.  
  
 ![Fluxo de trabalho de localização](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![Fluxo de trabalho não localizado](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>Exemplos de localização no WPF  
 Esta seção contém exemplos de aplicativos localizados para ajudá-lo a entender como construir e localizar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos.  
  
#### <a name="run-dialog-box-example"></a>Exemplo da caixa de diálogo Executar  
 Os gráficos a seguir mostram a saída de **executar** exemplo de caixa de diálogo.  
  
 **Inglês:**  
  
 ![Caixa de diálogo Executar](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **Alemão:**  
  
 ![Caixa de diálogo Executar em alemão](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **Criando uma caixa de diálogo Executar global**  
  
 Este exemplo produz uma **executar** caixa de diálogo usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Essa caixa de diálogo é equivalente ao **executar** caixa de diálogo está disponível a partir de [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] menu Iniciar.  
  
 Alguns destaques para a criação de caixas de diálogo globais são:  
  
 **Layout automático**  
  
 *Em Window1.xaml:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 A propriedade Window anterior redimensiona automaticamente a janela de acordo com o tamanho do conteúdo. Essa propriedade impede que a janela corte o conteúdo que aumenta de tamanho após a localização; ela também remove o espaço desnecessário quando o conteúdo diminui de tamanho após a localização.  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>propriedades são necessárias para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localização [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] funcione corretamente.  
  
 Eles são usados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localização [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] para controlar alterações entre o desenvolvimento e a localização do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>propriedades permitem a mesclagem de uma versão mais recente do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] com uma localização mais antiga do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Adicionar um <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedade executando **msbuild /t: updateuid RunDialog** em um shell de comando. Este é o método recomendado de adicionar <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades porque adicioná-las manualmente é normalmente demorado e menos preciso. Você pode verificar se <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriedades são definidas corretamente executando **msbuild checkuid RunDialog**.  
  
 O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é estruturado usando o <xref:System.Windows.Controls.Grid> controle, que é um controle útil para tirar proveito do layout automático no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Observe que a caixa de diálogo é dividida em três linhas e cinco colunas. Não uma das definições de linha e coluna tem um tamanho fixo; Portanto, o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos que são posicionados em cada célula podem adaptar a aumenta e diminui de tamanho durante a localização.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 As duas primeiras colunas onde o **abrir:** rótulo e <xref:System.Windows.Controls.ComboBox> são colocados usam 10 por cento do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] largura total.  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 Observe que o exemplo usa o recurso de dimensionamento compartilhado do <xref:System.Windows.Controls.Grid>. As três últimas colunas aproveitam isso colocando-se no mesmo <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Como normalmente se esperaria do nome da propriedade, isso permite que as colunas compartilhem o mesmo tamanho. Portanto, quando “Procurar...” é localizado para a cadeia de caracteres mais longa “Durchsuchen...”, todos os botões crescem em largura, em vez de haver um botão “OK” pequeno e um botão “Durchsuchen…” desproporcionalmente grande .  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 Observe o [XML: lang tratamento em XAML](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) colocado no elemento raiz da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Essa propriedade descreve a cultura de determinado elemento e seus filhos. Esse valor é usado por vários recursos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e deve ser alterado apropriadamente durante a localização. Esse valor altera qual dicionário de idioma deve ser usado para hifenizar e fazer a verificação ortográfica das palavras. Ele também afeta a exibição de dígitos e como o sistema de fallback de fontes seleciona qual fonte deve ser usada. Finalmente, a propriedade afeta a maneira como os números são exibidos e o modo como os textos escritos em scripts complexos são formatados. O valor padrão é “en-US”.  
  
 **Compilando um assembly de recursos satélite**  
  
 *Em .csproj:*  
  
 `<UICulture>en-US</UICulture>`  
  
 Observe a adição de uma `UICulture` valor. Quando isso é definido como uma opção válida <xref:System.Globalization.CultureInfo> valor como en-US, compilar o projeto irá gerar um assembly satélite com todos os recursos localizáveis nele.  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 O `RunIcon.JPG` não precisa ser localizado porque ele deve aparecer o mesmo para todas as culturas. `Localizable`é definido como `false` para que ele permaneça no idioma neutro assembly principal, em vez do assembly satélite. O valor padrão de todos os recursos não compiláveis é `Localizable` definido como `true`.  
  
 **Localizando a caixa de diálogo Executar**  
  
 **Analisar**  
  
 Depois de criar o aplicativo, a primeira etapa da localização é analisar os recursos localizáveis fora do assembly satélite. Para os fins deste tópico, use a ferramenta LocBaml de exemplo que pode ser encontrada em [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016). Observe que LocBaml é apenas uma ferramenta de exemplo para ajudá-lo a começar a criar uma ferramenta de localização que se ajuste ao seu processo de localização. Usando LocBaml, execute o seguinte para analisar: **LocBaml/analisar /Parse /out:** para gerar um arquivo "RunDialog".  
  
 **Localizar**  
  
 Use seu editor de CSV favorito que dá suporte a Unicode para editar esse arquivo. Filtre todas as entradas com a categoria de localização “Nenhum”. Você deverá ver as seguintes entradas:  
  
|Chave de Recurso|Categoria de Localização|Valor|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Botão|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Botão|Cancelar|  
|Button_3:System.Windows.Controls.Button.$Content|Botão|Procurar...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texto|Digite o nome de um programa, uma pasta, um documento ou recurso da Internet e o Windows o abrirá para você.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Texto|Abrir:|  
|Window_1:System.Windows.Window.Title|Título|Executar|  
  
 A localização do aplicativo para o alemão exigirá as seguintes traduções:  
  
|Chave de Recurso|Categoria de Localização|Valor|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|Botão|OK|  
|Button_2:System.Windows.Controls.Button.$Content|Botão|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|Botão|Durchsuchen…|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texto|Geben Sie den Namen eines Programms, Ordners, Dokuments oder einer Internetresource an.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Texto|Öffnen:|  
|Window_1:System.Windows.Window.Title|Título|Executar|  
  
 **Gerar**  
  
 A última etapa da localização envolve a criação do assembly satélite recém-localizado. Faça isso com o seguinte comando do LocBaml:  
  
 **LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**  
  
 Em alemão [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], se este Resources for colocado em uma pasta de-DE, ao lado do assembly principal, este recurso será carregado automaticamente em vez na pasta en-US. Se você não tiver uma versão em alemão de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] para testar isso, defina a cultura para qualquer cultura de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] você estiver usando (ou seja, en-US) e substitua o Resources original.  
  
 **Carregamento de recursos satélite**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|Código|BAML original em inglês|BAML localizado|  
|Recursos com neutralidade de cultura|Outros recursos em inglês|Outros recursos localizados para o alemão|  
  
 O .NET framework automaticamente escolhe qual assembly de recursos de satélite do aplicativo `Thread.CurrentThread.CurrentUICulture`. O padrão é a cultura do seu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sistema operacional. Portanto, se você estiver usando alemão [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], carrega o de-DE\MyDialog.resources.dll, se você estiver usando o inglês [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], carrega o en-US\MyDialog.resources.dll. É possível definir o recurso de fallback final para o aplicativo especificando o NeutralResourcesLanguage em AssemblyInfo* do projeto. Por exemplo, se você especificar:  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 o en-US\MyDialog.resources.dll será usado com o Windows em alemão se um de-DE\MyDialog.resources.dll ou de\MyDialog.resources.dll não estiver disponível.  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Home page da Microsoft na Arábia Saudita  
 Os gráficos a seguir mostram uma home page em inglês e em árabe. Para o exemplo completo que produz esses elementos gráficos, consulte [Globalization Homepage Sample](http://go.microsoft.com/fwlink/?LinkID=159990).  
  
 **Inglês:**  
  
 ![Página em inglês](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **Árabe:**  
  
 ![Página em árabe](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>Criando uma home page global da Microsoft  
 Este exemplo fictício do site da Microsoft na Arábia Saudita ilustra os recursos de globalização fornecidos para idiomas RightToLeft. Idiomas como árabe e hebraico têm uma ordem de leitura da direita para esquerda para o layout de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] geralmente deve ser dispostos bastante diferente do que seria em idiomas da esquerda para a direita como o inglês. A localização de um idioma da esquerda para a direita para um idioma da direita para a esquerda ou vice-versa pode apresentar muitos desafios. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] foi projetado para facilitar grande parte dessas localizações.  
  
 **FlowDirection**  
  
 *Homepage.xaml:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 Observe o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade <xref:System.Windows.Controls.Page>. A alteração dessa propriedade para <xref:System.Windows.FlowDirection.RightToLeft> alterará o <xref:System.Windows.FrameworkElement.FlowDirection%2A> do <xref:System.Windows.Controls.Page> e seus elementos filhos para que o layout deste [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é invertido para se tornar direita para esquerda como um usuário árabe esperaria. Pode substituir o comportamento de herança especificando uma explícita <xref:System.Windows.FrameworkElement.FlowDirection%2A> em qualquer elemento. O <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade está disponível em qualquer <xref:System.Windows.FrameworkElement> ou elemento relacionado a documentos e tem um valor implícito de <xref:System.Windows.FlowDirection.LeftToRight>.  
  
 Observe que mesmo os pincéis de gradiente do plano de fundo são invertidos corretamente quando a raiz <xref:System.Windows.FrameworkElement.FlowDirection%2A> é alterado:  
  
 **FlowDirection="LeftToRight"**  
  
 ![Fluxo da esquerda para a direita](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![Fluxo da direita para esquerda](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **Evitar usar dimensões fixas para painéis e controles**  
  
 Dê uma olhada em HomePage, observe que além de largura e altura fixas especificadas para toda a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] na parte superior <xref:System.Windows.Controls.DockPanel>, não há nenhum outras dimensões fixas. Evite usar dimensões fixas para evitar o recorte do texto localizado, que pode ser maior que o texto de origem. Os painéis e controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] serão automaticamente redimensionados de acordo com o conteúdo que eles contêm. A maioria dos controles também tem dimensões mínima e máxima que podem ser definidas para obter mais controle (ou seja, MinWidth= “20”). Com <xref:System.Windows.Controls.Grid>, você também pode definir larguras e alturas relativas usando ' *' (ou seja, Width = "0,25\*") ou usar seu tamanho de célula, o recurso de compartilhamento.  
  
 **Comentários de localização**  
  
 Há muitos casos em que o conteúdo pode ser ambíguo e difícil de ser traduzido. O desenvolvedor ou o designer tem a capacidade de fornecer um contexto extra e comentários para os localizadores por meio de comentários de localização. Por exemplo o Localization.Comments abaixo esclarece o uso do caractere “&#124;”.  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 Esse comentário fica associado ao conteúdo do TextBlock_1 e no caso da ferramenta LocBaml, (consulte [localizar um aplicativo](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)), ele pode ser visto em 6 de coluna da linha TextBlock_1 no arquivo. csv de saída:  
  
|Chave de Recurso|Categoria|Legível|Modificável|Comentário|Valor|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texto|TRUE|TRUE|Esse caractere é usado como uma regra decorativa.|&#124;|  
  
 Os comentários podem ser colocados no conteúdo ou na propriedade de qualquer elemento com a seguinte sintaxe:  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **Atributos de Localização**  
  
 De modo geral, o desenvolvedor ou o gerente de localização precisa controlar o que os localizadores podem ler e modificar. Por exemplo, talvez você não deseje que o localizador traduza o nome de sua empresa ou palavras que se referem ao conteúdo legal. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece atributos que permitem definir a legibilidade, modificabilidade e categoria do conteúdo ou da propriedade de um elemento que a ferramenta de localização pode usar para bloquear, ocultar ou classificar elementos. Para obter mais informações, consulte <xref:System.Windows.Localization.Attributes%2A>. Para as finalidades desta amostra, a ferramenta LocBaml somente gera os valores desses atributos. Todos os controles do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm valores padrão para esses atributos, mas eles podem ser substituídos. Por exemplo, o exemplo a seguir substitui os atributos padrão de localização para `TextBlock_1` e define o conteúdo esteja legível mas não modificável para os localizadores.  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 Além de atributos de leitura e modificação, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma enumeração das categorias comuns de interface do usuário (<xref:System.Windows.LocalizationCategory>) que pode ser usado para fornecer mais contexto aos localizadores. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] categorias padrão para controles de plataforma podem ser substituídas na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] também:  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 A localização padrão de atributos que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece também pode ser substituído pelo código, você pode definir corretamente os valores padrão certos para controles personalizados. Por exemplo:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 Os atributos de instância definidos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] terá precedência sobre os valores definidos no código em controles personalizados. Para obter mais informações sobre atributos e comentários, consulte [atributos de localização e comentários](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
 **Fallback de fontes e fontes de composição**  
  
 Se você especificar uma fonte que não oferece suporte a um intervalo de determinado codepoint [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automaticamente alternará para uma que faz usando o compositefont Global do usuário que está localizado na pasta Windows\Fonts. Fontes de composição funcionam como qualquer outra fonte e podem ser usadas explicitamente configurando a FontFamily de um elemento (ou seja, FontFamily= “Global User Interface”). Você pode especificar sua própria preferência de fallback de fontes criando sua própria fonte de composição e especificando qual fonte será usada para intervalos de ponto de código e idiomas específicos.  
  
 Para obter mais informações sobre fontes compostas consulte <xref:System.Windows.Media.FontFamily>.  
  
 **Localizando a home page da Microsoft**  
  
 É possível seguir as mesmas etapas do exemplo da Caixa de Diálogo Executar para localizar esse aplicativo. O arquivo. csv localizado para árabe está disponível para você no [Globalization Homepage Sample](http://go.microsoft.com/fwlink/?LinkID=159990).
