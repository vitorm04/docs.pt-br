---
title: Compilando um aplicativo WPF (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], building
ms.assetid: a58696fd-bdad-4b55-9759-136dfdf8b91c
ms.openlocfilehash: 89ceb39b08250bc400eed6ca8f8c24013446b453
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417285"
---
# <a name="building-a-wpf-application-wpf"></a>Compilando um aplicativo WPF (WPF)
Aplicativos do Windows Presentation Foundation (WPF) podem ser criados como [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] executáveis (.exe), bibliotecas (. dll) ou uma combinação de ambos os tipos de assemblies. Este tópico apresenta como compilar aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e descreve as principais etapas no processo de build.  
  
  
<a name="Building_a_WPF_Application_using_Command_Line"></a>   
## <a name="building-a-wpf-application"></a>Compilando um aplicativo WPF  
 Um aplicativo WPF pode ser compilado das seguintes maneiras:  
  
-   Linha de comando. O aplicativo deve conter somente código (sem XAML) e um arquivo de definição de aplicativo. Para obter mais informações, consulte [Build pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build na linha de comando (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
-   MSBuild (Microsoft Build Engine). Além do código e de arquivos XAML, o aplicativo deve conter um arquivo de projeto do MSBuild. Para mais informações, consulte "MSBuild".  
  
-   Visual Studio. O Visual Studio é um ambiente de desenvolvimento integrado que compila aplicativos WPF com o MSBuild e inclui um designer visual para a criação da interface do usuário. Para obter mais informações, consulte [desenvolvimento de aplicativos no Visual Studio](https://msdn.microsoft.com/library/97490c1b-a247-41fb-8f2c-bc4c201eff68) e [Design XAML no Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
<a name="The_Windows_Presentation_Foundation_Build_Pipeline"></a>   
## <a name="wpf-build-pipeline"></a>Pipeline de build do WPF  
 Quando um projeto do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] é compilado, a combinação de destinos específicos a um idioma e específicos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] são invocados. O processo de execução desses destinos denomina-se pipeline de build, e as principais etapas estão ilustradas na figura a seguir.  
  
 ![Processo de build do WPF](../../../../docs/framework/wpf/app-development/media/wpfbuildsystem-figure1.png "WPFBuildSystem_Figure1")  
  
<a name="Pre_Build_Initializations"></a>   
### <a name="pre-build-initializations"></a>Inicializações pré-build  
 Antes de compilar, o [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] determina a localização das ferramentas e bibliotecas importantes, incluindo o seguinte:  
  
-   O .NET Framework.  
  
-   Os diretórios de [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)].  
  
-   O local dos assemblies de referência do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   A propriedade para os caminhos de pesquisa de assembly.  
  
 O primeiro local em que o [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] procura assemblies é o diretório do assembly de referência (%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.0\\). Durante essa etapa, o processo de build também inicializa as várias propriedades e grupos de itens e realiza qualquer trabalho necessário de limpeza.  
  
<a name="Resolving_references"></a>   
### <a name="resolving-references"></a>Resolvendo referências  
 O processo de build localiza e associa os assemblies necessários para compilar o projeto de aplicativo. Essa lógica está contida na tarefa `ResolveAssemblyReference`. Todos os assemblies declarados como `Reference` no arquivo de projeto são fornecidos para a tarefa, junto com as informações sobre os caminhos de pesquisa e metadados sobre os assemblies já instalados no sistema. A tarefa procura assemblies e usa os metadados do assembly instalado para filtrar os principais assemblies do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] que não precisam aparecer nos manifestos de saída. Isso é feito para evitar informações redundantes nos manifestos do ClickOnce. Por exemplo, uma vez que PresentationFramework. dll pode ser considerado representativo de um aplicativo compilado no e para o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e, além disso já que todos os [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assemblies existir no mesmo local em cada computador que tem o .NET Framework não é instalado, é necessário incluir todas as informações sobre todos os assemblies de referência do .NET Framework nos manifestos.  
  
<a name="Markup_Compilation___Pass_1"></a>   
### <a name="markup-compilationpass-1"></a>Compilação de marcação — passo 1  
 Nesta etapa, os arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são analisados e compilados de modo que o tempo de execução não gaste tempo analisando [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] e validando valores da propriedade. O arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compilado é pré-indexado para que, em tempo de execução, seu carregamento seja muito mais rápido do que carregar um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Durante esta etapa, as seguintes atividades ocorrem para cada arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que é um item de build `Page`:  
  
1.  O arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é analisado pelo compilador de marcação.  
  
2.  Uma representação compilada é criada para esse [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e copiada para a pasta obj\Release.  
  
3.  Uma representação CodeDOM de uma nova classe parcial é criada e copiada para a pasta obj\Release.  
  
 Além disso, um arquivo de código específico a um idioma é gerado para cada arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Por exemplo, para uma página Page1.xaml em um projeto do Visual Basic, é gerado um Page1.g.vb; para uma página Page1.xaml em um projeto c#, um Page1.g.cs é gerado. O ".g" no nome de arquivo indica que o arquivo é um código gerado que tem uma declaração de classe parcial para o elemento de nível superior do arquivo de marcação (como `Page` ou `Window`). A classe é declarada com o `partial` modificador em c# (`Extends` no Visual Basic) para indicar que há outra declaração para a classe em outro lugar, geralmente no code-behind do arquivo Page1.xaml.cs.  
  
 A classe parcial estende a classe base apropriada (como <xref:System.Windows.Controls.Page> para uma página) e implementa o <xref:System.Windows.Markup.IComponentConnector?displayProperty=nameWithType> interface. O <xref:System.Windows.Markup.IComponentConnector> interface tem métodos para inicializar um componente e conectar nomes e eventos aos elementos em seu conteúdo. Consequentemente, o arquivo de código gerado tem uma implementação de método semelhante à seguinte:  
  
```csharp  
public void InitializeComponent() {  
    if (_contentLoaded) {  
        return;  
    }  
    _contentLoaded = true;  
    System.Uri resourceLocater =   
        new System.Uri(  
            "window1.xaml",   
            System.UriKind.RelativeOrAbsolute);  
    System.Windows.Application.LoadComponent(this, resourceLocater);  
}  
```  
  
```vb  
Public Sub InitializeComponent() _  
  
    If _contentLoaded Then  
        Return  
    End If  
  
    _contentLoaded = True  
    Dim resourceLocater As System.Uri = _  
        New System.Uri("mainwindow.xaml", System.UriKind.Relative)  
  
    System.Windows.Application.LoadComponent(Me, resourceLocater)  
  
End Sub  
```  
  
 Por padrão, a compilação de marcação é executado no mesmo <xref:System.AppDomain> como o [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] mecanismo. Isso proporciona ganhos significativos de desempenho. Esse comportamento pode ser alternado com a propriedade `AlwaysCompileMarkupFilesInSeparateDomain`. Isso tem a vantagem de descarregar todos os assemblies de referência através do descarregamento separada <xref:System.AppDomain>.  
  
<a name="Pass_2_of_Markup_Compilation"></a>   
### <a name="markup-compilationpass-2"></a>Compilação de marcação — passo 2  
 Nem todos as páginas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são compiladas durante o passo 1 da compilação de marcação. Os arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que têm referências de tipo definidas localmente (referências a tipos definidos no código em outro local do mesmo projeto) são isentos de compilação nesse momento. Isso ocorre porque esses tipos definidos localmente existem somente na fonte e ainda não foram compilados. Para determinar isso, o analisador usa heurísticas que envolvem a procura de itens como `x:Name` no arquivo de marcação. Quando uma instância dessas é encontrada, a compilação desse arquivo de marcação é adiada até que os arquivos de código tenham sido compilados, e depois disso, o segundo passo da compilação da marcação processa esses arquivos.  
  
<a name="File_Classification"></a>   
### <a name="file-classification"></a>Classificação de arquivos  
 O processo de build coloca arquivos de saída em diferentes grupos de recursos com base em qual assembly de aplicativo eles serão colocados. Em um aplicativo típico não localizado, todos os arquivos de dados marcados como `Resource` são colocados no assembly principal (executável ou biblioteca). Quando a `UICulture` é definida no projeto, todos os arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compilados e os recursos especificamente marcados como específicos a um idioma, são colocados no assembly de recursos satélite. Além disso, todos os recursos com neutralidade de idioma são colocados no assembly principal. Essa determinação é feita nessa etapa do processo de build.  
  
 As ações de build `ApplicationDefinition`, `Page`, e `Resource` no arquivo de projeto podem ser aumentadas com os metadados `Localizable` (os valores aceitáveis são `true` e `false`), que determinam se o arquivo é específico a um idioma ou com neutralidade de idioma.  
  
<a name="Core_Compilation"></a>   
### <a name="core-compilation"></a>Compilação principal  
 A etapa de compilação principal envolve a compilação de arquivos de código. Isso é orquestrado por lógica nos arquivos de destinos específicos a um idioma Microsoft.CSharp.targets e Microsoft.VisualBasic.targets. Se as heurísticas determinarem que uma única passagem do compilador de marcação é suficiente, então o assembly principal será gerado. No entanto, se um ou mais arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] no projeto têm referências a tipos definidos localmente, um arquivo .dll temporário é gerado para que os assemblies do aplicativo final possam ser criados depois que a segunda passagem da compilação de marcação estiver concluída.  
  
<a name="Manifest_generation"></a>   
### <a name="manifest-generation"></a>Geração de manifesto  
 Ao final do processo de build, quando todos os assemblies de aplicativo e arquivos de conteúdo estiverem prontos, os manifestos do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] para o aplicativo são gerados.  
  
 O arquivo de manifesto de implantação descreve o modelo de implantação: a versão atual, o comportamento de atualização e a identidade do editor junto com a assinatura digital. Esse manifesto deve ser criado pelos administradores que lidam com a implantação. A extensão de arquivo é .xbap (para o [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]) e .application para aplicativos instalados. A primeira é determinada pela propriedade do projeto `HostInBrowser` e, como resultado, o manifesto identifica o aplicativo como hospedado pelo navegador.  
  
 O manifesto do aplicativo (um arquivo de manifesto .exe) descreve os assemblies do aplicativo e as bibliotecas dependentes e permissões de lista exigidas pelo aplicativo. Esse arquivo deve ser criado pelo desenvolvedor do aplicativo. Para a inicialização de um aplicativo do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], um usuário abre o arquivo de manifesto de implantação do aplicativo.  
  
 Esses arquivos de manifesto são sempre criados para o [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Para aplicativos instalados, eles não são criados, a menos que a propriedade `GenerateManifests` seja especificada no arquivo de projeto com o valor `true`.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] obter duas permissões adicionais além das permissões atribuídas a aplicativos típicos da zona da Internet: <xref:System.Security.Permissions.WebBrowserPermission> e <xref:System.Security.Permissions.MediaPermission>. O sistema de build do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] declara essas permissões no manifesto do aplicativo.  
  
<a name="Incremental_Build_Support"></a>   
## <a name="incremental-build-support"></a>Suporte ao build incremental  
 O sistema de build do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dá suporte para builds incrementais. Ele é bastante inteligente para detectar as alterações feitas na marcação ou no código, e ele compila somente os artefatos afetados pela alteração. O mecanismo de build incremental usa os seguintes arquivos:  
  
-   Um arquivo $(*AssemblyName*)_MarkupCompiler.Cache para manter o estado atual do compilador.  
  
-   Um arquivo $(*AssemblyName*)_MarkupCompiler.lref para armazenar em cache os arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] com referências a tipos definidos localmente.  
  
 Abaixo está um conjunto de regras que rege o build incremental:  
  
-   O arquivo é a menor unidade na qual o sistema de build detecta alterações. Portanto, para um arquivo de código, o sistema de build não pode determinar se um tipo foi alterado ou se algum código foi adicionado. O mesmo ocorre para arquivos de projeto.  
  
-   O mecanismo de build incremental deve estar ciente de que uma página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] define uma classe ou usa outras classes.  
  
-   Se entradas `Reference` forem alteradas, recompilar todas as páginas.  
  
-   Se um arquivo de código for alterado, recompilar todas as páginas com referências de tipo definidas localmente.  
  
-   Se um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for alterado:  
  
    -   Se o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é declarado como `Page` no projeto: se o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] não tem referências de tipo definidas localmente, recompilar aquele [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mais todas as páginas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] com referências locais. Se o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tem referências locais, recompilar todas as páginas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] com referências locais.  
  
    -   Se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é declarado como `ApplicationDefinition` no projeto: recompilar todas as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] páginas (motivo: cada [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tem referência a um <xref:System.Windows.Application> tipo que pode ter sido alterado).  
  
-   Se o arquivo de projeto declara um arquivo de código como definição de aplicativo em vez de um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
    -   Verifique se o valor `ApplicationClassName` no arquivo de projeto foi alterado (existe um novo tipo de aplicativo?). Em caso afirmativo, recompilar o aplicativo inteiro.  
  
    -   Caso contrário, recompilar todas as páginas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] com referências locais.  
  
-   Se um arquivo de projeto for alterado: aplique todas as regras anteriores e veja o que precisa ser recompilado. As alterações nas seguintes propriedades disparam uma recompilação completa: `AssemblyName`, `IntermediateOutputPath`, `RootNamespace` e `HostInBrowser`.  
  
 Os seguintes cenários de recompilação são possíveis:  
  
-   Todo o aplicativo é recompilado.  
  
-   Somente os arquivos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que têm referências de tipo definidas localmente são recompilados.  
  
-   Nada é recompilado (se nada no projeto tiver sido alterado).  
  
## <a name="see-also"></a>Consulte também  
 [Implantando um aplicativo WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Referência do WPF MSBuild](/visualstudio/msbuild/wpf-msbuild-reference)  
 [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
