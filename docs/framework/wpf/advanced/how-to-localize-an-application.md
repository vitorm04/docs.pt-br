---
title: Como localizar um aplicativo
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ed8ee8b8bfd9c3d6dadfedad8889af10a86466
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-localize-an-application"></a>Como localizar um aplicativo
Esse tutorial explica como criar um aplicativo localizado usando a ferramenta LocBaml.  
  
> [!NOTE]
>  A ferramenta LocBaml não é um aplicativo pronto para produção. Ela é apresentada como um exemplo que usa algumas das APIs de localização e ilustra como você pode escrever uma ferramenta de localização.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Visão geral  
 Esta discussão oferece uma abordagem passo a passo para a localização de um aplicativo. Primeiro, você preparará o seu aplicativo para que o texto que será convertido possa ser extraído. Depois que o texto for traduzido, você o mesclará em uma nova cópia do aplicativo original.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Requisitos  
 No decorrer desta discussão, você usará [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], que é um compilador que é executado na linha de comando.  
  
 Além disso, você será instruído a usar um arquivo de projeto. Para obter instruções sobre como usar [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] e arquivos de projeto, consulte [compilar e implantar](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 Todos os exemplos nesta discussão usam en-US (inglês-EUA) como a cultura. Isso permite que você trabalhe nas etapas dos exemplos sem instalar um idioma diferente.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Criar um aplicativo de exemplo  
 Nesta etapa, você preparará seu aplicativo para a localização. No [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] exemplos, um HelloApp de exemplo é fornecido que será usado para os exemplos de código nesta discussão. Se você quiser usar esse exemplo, baixe o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivos do [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Desenvolva seu aplicativo até o ponto em que você deseja iniciar a localização.  
  
2.  Especifique o idioma de desenvolvimento no arquivo de projeto para que [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] gera um assembly principal e um assembly satélite (um arquivo com o. Resources extensão) para conter os recursos de idioma neutro. O arquivo de projeto no exemplo HelloApp é o HelloApp.csproj. Nesse arquivo, você encontrará a linguagem de desenvolvimento identificada da seguinte maneira:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  Adicione Uids a sua [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivos. Os Uids são usados para controlar as alterações nos arquivos e para identificar os itens que devem ser traduzidos. Para adicionar Uids em seus arquivos, execute **updateuid** em seu arquivo de projeto:  
  
     **msbuild /t:updateuid helloapp.csproj**  
  
     Para verificar se estão ausentes ou duplicados Uids, execute **checkuid**:  
  
     **msbuild /t:checkuid helloapp.csproj**  
  
     Depois de executar **updateuid**, seus arquivos devem conter Uids. Por exemplo, no arquivo Pane1.xaml do HelloApp, você deve encontrar o seguinte:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Criar o assembly satélite de recursos de idioma neutro  
 Depois que o aplicativo está configurado para gerar um assembly satélite de recursos de idioma neutro, você compila o aplicativo. Isso gera o assembly principal do aplicativo, bem como o assembly satélite de recursos de idioma neutro exigido pela LocBaml para a localização. Para compilar o aplicativo:  
  
1.  Compile HelloApp para criar um [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **msbuild helloapp.csproj**  
  
2.  O assembly principal recém-criado do aplicativo, HelloApp.exe, é criado na seguinte pasta:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  O assembly satélite de recursos de idioma neutro recém-criado, HelloApp.resources.dll, é criado na seguinte pasta:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Compilar a ferramenta LocBaml  
  
1.  Todos os arquivos necessários para compilar LocBaml estão localizados no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exemplos. Baixe o [!INCLUDE[TLA#tla_lhcshrp](../../../../includes/tlasharptla-lhcshrp-md.md)] arquivos do [LocBaml Tool Sample](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  Na linha de comando, execute o arquivo de projeto (locbaml.csproj) para compilar a ferramenta:  
  
     **msbuild locbaml.csproj**  
  
3.  Acesse o diretório Bin\Release para encontrar o arquivo executável recém-criado (locbaml.exe). Exemplo: C:\LocBaml\Bin\Release\locbaml.exe.  
  
4.  As opções que você pode especificar ao executar a LocBaml são as seguintes:  
  
    -   **Analisar** ou **-p:** Baml analisa, recursos, ou [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] arquivos para gerar um arquivo. csv ou. txt.  
  
    -   **Gerar** ou **-g** gera um arquivo binário localizado usando um arquivo traduzido.  
  
    -   **out** ou **-o** {*filedirectory*] **:** nome do arquivo de saída.  
  
    -   **cultura** ou **- cul** {*cultura*] **:** localidade dos assemblies de saída.  
  
    -   **tradução** ou **- trans** {*tradução. csv*] **:** arquivo traduzido ou localizado.  
  
    -   **asmpath** ou **- asmpath:** {*filedirectory*] **:** se seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] código contém controles personalizados, você deve fornecer o  **asmpath** para o assembly de controle personalizado.  
  
    -   **nologo:** não exibe nenhuma informação de logotipo ou direitos autorais.  
  
    -   **verbose:** exibe informações de modo detalhado.  
  
    > [!NOTE]
    >  Se precisar de uma lista de opções quando você estiver executando a ferramenta, digite **LocBaml.exe** e pressione ENTER.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Usar LocBaml para analisar um arquivo  
 Agora que criou a ferramenta LocBaml, você está pronto para usá-la para analisar o HelloApp.resources.dll e extrair o conteúdo de texto que será localizado.  
  
1.  Copie o LocBaml.exe para a pasta bin\debug do aplicativo, em que o assembly principal do aplicativo foi criado.  
  
2.  Para analisar o arquivo do assembly satélite e armazenar o resultado como um arquivo .csv, use o seguinte comando:  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  Se o arquivo de entrada, HelloApp.resources.dll, não estiver no mesmo diretório que o LocBaml.exe mova um dos arquivos para que ambos estejam no mesmo diretório.  
  
3.  Ao executar a LocBaml para analisar arquivos, a saída consistirá em sete campos delimitados por vírgulas (arquivos .csv) ou tabulações (arquivos .txt). A seguir está o arquivo .csv analisado do HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Os sete campos são:  
  
   1.  **Nome BAML**. O nome do recurso BAML em relação ao assembly satélite do idioma de origem.  
  
   2.  **Chave de recurso**. O identificador do recurso localizado.  
  
   3.  **Categoria**. O tipo de valor. Consulte [atributos de localização e comentários](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Legibilidade**. Se o valor pode ser lido por um localizador. Consulte [atributos de localização e comentários](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modificabilidade**. Se o valor pode ser modificado por um localizador. Consulte [atributos de localização e comentários](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Comentários**. Descrição adicional do valor para ajudar a determinar como um valor é localizado. Consulte [atributos de localização e comentários](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Valor**. O valor de texto a traduzir para a cultura desejada.  
  
   A tabela a seguir mostra como esses campos são mapeados para os valores delimitados do arquivo .csv:  
  
   |Nome BAML|Chave de recurso|Categoria|Legibilidade|Modificabilidade|Comentários|Valor|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorar|FALSE|FALSE||Texto&#1; # Texto2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Nenhum|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Nenhum|TRUE|TRUE||Goodbye World|
  
   Observe que todos os valores para o **comentários** campo não contêm nenhum valor; se um campo não tiver um valor, ele está vazio. Observe também que o item na primeira linha não é legível nem modificável e tem "Ignore" como seu **categoria** valor, que indica que o valor não é localizável.  
  
4.  Para facilitar a descoberta de itens localizáveis em arquivos analisados, especialmente em grandes arquivos, você pode classificar ou filtrar itens por **categoria**, **legibilidade**, e **modificação**. Por exemplo, você pode filtrar valores e ilegíveis e não modificáveis.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Traduzir o conteúdo localizável  
 Use qualquer ferramenta que você tiver disponível para traduzir o conteúdo extraído. Uma boa maneira de fazer isso é gravar arquivo de recursos para um arquivo. csv e exibi-las no [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], fazer conversão muda para a última coluna (valor).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Usar a LocBaml para gerar um novo arquivo .resources.dll  
 O conteúdo que foi identificado ao analisar o HelloApp.resources.dll com a LocBaml foi traduzido e deve ser mesclado de volta no aplicativo original. Use o **gerar** ou **-g** opção para gerar um novo. arquivo Resources.  
  
1.  Use a seguinte sintaxe para gerar um novo arquivo HelloApp.resources.dll. Marque a cultura como en-US (/cul:en-US).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    >  Se o arquivo de entrada, Hello.csv, não estiver no mesmo diretório que o executável, LocBaml.exe, mova um dos arquivos para que ambos estejam no mesmo diretório.  
  
2.  Substitua o arquivo HelloApp.resources.dll no diretório C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll antigo pelo arquivo HelloApp.resources.dll recém-criado.  
  
3.  "Hello World" e "Goodbye World" agora devem estar traduzidos em seu aplicativo.  
  
4.  Para traduzir para uma cultura diferente, use a cultura do idioma para o qual você está traduzindo. O exemplo a seguir mostra como traduzir para francês canadense:  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5.  No mesmo assembly que o assembly principal do aplicativo, crie uma nova pasta específica de cultura para abrigar o novo assembly satélite. Para francês canadense, a pasta seria fr-CA.  
  
6.  Copie o assembly satélite gerado para a nova pasta.  
  
7.  Para testar o novo assembly satélite, você precisa alterar a cultura na qual o aplicativo será executado. Você pode fazer isso de duas maneiras:  
  
    -   Alterar as configurações regionais do seu sistema operacional (**iniciar** &#124; **Painel de controle** &#124; **Opções regionais e idiomas**).  
  
    -   Em seu aplicativo, adicione o seguinte código em App.xaml.cs:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Algumas dicas para usar a LocBaml  
  
-   Todos os assemblies dependentes que definem controles personalizados devem ser copiados para o diretório local da LocBaml ou instalados no GAC. Isso é necessário porque a API de localização deve ter acesso aos assemblies dependentes quando ele lê o [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Se o assembly principal é assinado, a DLL de recurso gerado também deve ser assinada para que seja carregada.  
  
-   A versão da DLL de recurso localizado precisa ser sincronizada com o assembly principal.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Novidades  
 Agora você deve ter um entendimento básico de como usar a ferramenta LocBaml.  Você deve ser capaz de criar um arquivo que contém Uids. Ao usar a ferramenta LocBaml, você deverá ser capaz de analisar um arquivo para extrair o conteúdo localizável e, depois que o conteúdo for traduzido, você deverá ser capaz de gerar um arquivo .resources.dll que mescla o conteúdo traduzido. Este tópico não inclui todos os detalhes possíveis, mas agora você tem o conhecimento necessário para usar a LocBaml na localização de seus aplicativos.  
  
## <a name="see-also"></a>Consulte também  
 [Globalização para WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Visão geral do uso de layout automático](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
