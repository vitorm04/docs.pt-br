---
title: Localizar um aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209676"
---
# <a name="how-to-localize-an-application"></a>Como localizar um aplicativo

Esse tutorial explica como criar um aplicativo localizado usando a ferramenta LocBaml.  
  
> [!NOTE]
> A ferramenta LocBaml não é um aplicativo pronto para produção. Ela é apresentada como um exemplo que usa algumas das APIs de localização e ilustra como você pode escrever uma ferramenta de localização.  
  
## <a name="overview"></a>Visão geral

Este artigo fornece uma abordagem passo a passo para a localização de um aplicativo. Primeiro, você prepara seu aplicativo para que o texto que será traduzido possa ser extraído. Depois que o texto é traduzido, você mescla o texto traduzido em uma nova cópia do aplicativo original.
  
## <a name="create-a-sample-application"></a>Criar um aplicativo de exemplo

Nesta etapa, você prepara seu aplicativo para localização. Nos exemplos de Windows Presentation Foundation (WPF), é fornecido um exemplo de HelloApp que será usado para os exemplos de código nesta discussão. Se você quiser usar este exemplo, baixe os arquivos de Extensible Application Markup Language (XAML) do exemplo da [ferramenta LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Desenvolva seu aplicativo até o ponto em que você deseja iniciar a localização.  
  
2. Especifique a linguagem de desenvolvimento no arquivo de projeto para que o MSBuild gere um assembly principal e um assembly satélite (um arquivo com a extensão. Resources. dll) para conter os recursos de idioma neutro. O arquivo de projeto no exemplo HelloApp é o HelloApp.csproj. Nesse arquivo, você encontrará a linguagem de desenvolvimento identificada da seguinte maneira:  
  
   `<UICulture>en-US</UICulture>`  
  
3. Adicione UIDs aos seus arquivos XAML. Os Uids são usados para controlar as alterações nos arquivos e para identificar os itens que devem ser traduzidos. Para adicionar UIDs aos seus arquivos, execute `updateuid` em seu arquivo de projeto:  

   `msbuild -t:updateuid helloapp.csproj`

   Para verificar se você não tem UIDs ausentes ou duplicados, execute `checkuid` :  

   `msbuild -t:checkuid helloapp.csproj`

   Após `updateuid` a execução, os arquivos devem conter UIDs. Por exemplo, no arquivo *Pane1. XAML* de HelloApp, você deve encontrar o seguinte:  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Criar o assembly satélite de recursos de idioma neutro

Depois que o aplicativo é configurado para gerar um assembly satélite de recursos de idioma neutro, você cria o aplicativo. Isso gera o assembly do aplicativo principal, bem como o assembly satélite de recursos de idioma neutro que é exigido por LocBaml para localização.

Para criar o aplicativo:  
  
1. Compile HelloApp para criar uma DLL (biblioteca de vínculo dinâmico):  
  
   `msbuild helloapp.csproj`
  
2. O assembly de aplicativo principal recém-criado, HelloApp. exe, é criado na seguinte pasta: *C:\HelloApp\Bin\Debug*
  
3. O assembly satélite de recursos de idioma neutro recentemente criado, HelloApp. Resources. dll, é criado na seguinte pasta: *C:\HelloApp\Bin\Debug\en-US*
  
## <a name="build-the-locbaml-tool"></a>Criar a ferramenta LocBaml  
  
1. Todos os arquivos necessários para compilar LocBaml estão localizados nos exemplos do WPF. Baixe os arquivos C# do [exemplo da ferramenta LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
2. Na linha de comando, execute o arquivo de projeto (locbaml.csproj) para compilar a ferramenta:  

   `msbuild locbaml.csproj`
  
3. Vá para o diretório *bin\Release* para localizar o arquivo executável recém-criado (LocBaml. exe). Exemplo: *C:\LocBaml\Bin\Release\locbaml.exe*
  
4. As opções que você pode especificar ao executar LocBaml são as seguintes.

   | Opção | Descrição|
   | - | - |
   | `parse` ou `-p` | Analisa arquivos BAML, recursos ou DLL para gerar um arquivo. csv ou. txt. |
   | `generate` ou `-g` | Gera um arquivo binário localizado usando um arquivo traduzido. |
   | `out`ou `-o` {*fileDirectory*] | Nome do arquivo de saída. |
   | `culture`ou `-cul` {*Culture*] | Localidade dos assemblies de saída. |
   | `translation`ou `-trans` {*translation. csv*] | Arquivo traduzido ou localizado. |
   | `asmpath`ou `-asmpath` {*fileDirectory*] | Se o código XAML contiver controles personalizados, você deverá fornecer o `asmpath` ao assembly de controle personalizado. |
   | `nologo` | Não exibe nenhum logotipo ou informações de direitos autorais. |
   | `verbose` | Exibe informações de modo detalhado. |
  
   > [!NOTE]
   > Se você precisar de uma lista das opções ao executar a ferramenta, digite `LocBaml.exe` e pressione **Enter**.
  
## <a name="use-locbaml-to-parse-a-file"></a>Usar LocBaml para analisar um arquivo

Agora que criou a ferramenta LocBaml, você está pronto para usá-la para analisar o HelloApp.resources.dll e extrair o conteúdo de texto que será localizado.  
  
1. Copie o LocBaml.exe para a pasta bin\debug do aplicativo, em que o assembly principal do aplicativo foi criado.  
  
2. Para analisar o arquivo do assembly satélite e armazenar o resultado como um arquivo .csv, use o seguinte comando:  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > Se o arquivo de entrada, HelloApp.resources.dll, não estiver no mesmo diretório que o LocBaml.exe mova um dos arquivos para que ambos estejam no mesmo diretório.  
  
3. Ao executar a LocBaml para analisar arquivos, a saída consistirá em sete campos delimitados por vírgulas (arquivos .csv) ou tabulações (arquivos .txt). A seguir está o arquivo .csv analisado do HelloApp.resources.dll:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Os sete campos são:  
  
   - **Nome de BAML**. O nome do recurso BAML em relação ao assembly satélite do idioma de origem.  
  
   - **Chave de recurso**. O identificador do recurso localizado.  
  
   - **Categoria**. O tipo de valor. Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).  
  
   - **Legibilidade**. Se o valor pode ser lido por um localizador. Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).  
  
   - **Modificabilidade**. Se o valor pode ser modificado por um localizador. Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).  
  
   - **Comentários**. Descrição adicional do valor para ajudar a determinar como um valor é localizado. Consulte [atributos e comentários de localização](localization-attributes-and-comments.md).  
  
   - **Valor**. O valor de texto a traduzir para a cultura desejada.  
  
   A tabela a seguir mostra como esses campos são mapeados para os valores delimitados do arquivo .csv:  
  
   |Nome BAML|Chave de recurso|Categoria|Legibilidade|Modificabilidade|Comentários|Valor|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorar|FALSE|FALSE||#Text1; #Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Nenhum|TRUE|TRUE||Olá, Mundo|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Nenhum|TRUE|TRUE||Goodbye World|
  
   Observe que todos os valores do campo **comentários** não contêm valores; se um campo não tiver um valor, ele estará vazio. Observe também que o item na primeira linha não é legível nem modificável e tem "ignorar" como seu valor de **categoria** , que indica que o valor não é localizável.  
  
4. Para facilitar a descoberta de itens localizáveis em arquivos analisados, especialmente em arquivos grandes, você pode classificar ou filtrar os itens por **categoria**, **legibilidade**e **modificação**. Por exemplo, você pode filtrar valores e ilegíveis e não modificáveis.  
  
## <a name="translate-the-localizable-content"></a>Traduza o conteúdo localizável

Use qualquer ferramenta que você tiver disponível para traduzir o conteúdo extraído. Uma boa maneira de fazer isso é gravar os recursos em um arquivo. csv e exibi-los no Microsoft Excel, fazendo alterações de tradução na última coluna (valor).  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Use LocBaml para gerar um novo arquivo. Resources. dll

O conteúdo que foi identificado ao analisar o HelloApp.resources.dll com a LocBaml foi traduzido e deve ser mesclado de volta no aplicativo original. Use a `generate` `-g` opção ou para gerar um novo arquivo. Resources. dll.  
  
1. Use a seguinte sintaxe para gerar um novo arquivo HelloApp.resources.dll. Marque a cultura como en-US (/cul:en-US).  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > Se o arquivo de entrada, Hello.csv, não estiver no mesmo diretório que o executável, LocBaml.exe, mova um dos arquivos para que ambos estejam no mesmo diretório.  
  
2. Substitua o antigo arquivo *HelloApp. Resources. dll* no diretório *C:\HelloApp\Bin\Debug\en-US\HelloApp.Resources.dll* pelo arquivo *HelloApp. Resources. dll* recém-criado.  
  
3. "Hello World" e "Goodbye World" agora devem estar traduzidos em seu aplicativo.  
  
4. Para traduzir para uma cultura diferente, use a cultura do idioma para o qual você está traduzindo. O exemplo a seguir mostra como traduzir para francês canadense:  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. No mesmo assembly que o assembly principal do aplicativo, crie uma nova pasta específica de cultura para abrigar o novo assembly satélite. Para francês canadense, a pasta seria fr-CA.  
  
6. Copie o assembly satélite gerado para a nova pasta.  
  
7. Para testar o novo assembly satélite, você precisa alterar a cultura na qual o aplicativo será executado. É possível fazer isso de duas formas:  
  
   - Altere as configurações regionais do seu sistema operacional.
  
   - Em seu aplicativo, adicione o seguinte código em App.xaml.cs:  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a>Dicas para usar LocBaml  
  
- Todos os assemblies dependentes que definem controles personalizados devem ser copiados para o diretório local da LocBaml ou instalados no GAC. Isso é necessário porque a API de localização deve ter acesso aos assemblies dependentes quando ele lê o XAML binário (BAML).  
  
- Se o assembly principal é assinado, a DLL de recurso gerado também deve ser assinada para que seja carregada.  
  
- A versão da DLL de recurso localizado precisa ser sincronizada com o assembly principal.
  
## <a name="see-also"></a>Confira também

- [Globalização do WPF](globalization-for-wpf.md)
- [Visão geral do uso de layout automático](use-automatic-layout-overview.md)
