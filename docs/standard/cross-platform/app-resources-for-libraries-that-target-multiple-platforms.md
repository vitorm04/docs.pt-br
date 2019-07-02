---
title: Recursos do aplicativo para bibliotecas direcionadas a várias plataformas
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e846f45b55ac09d6ce6af4f3223c3bdba1dc83ba
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506018"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Recursos do aplicativo para bibliotecas direcionadas a várias plataformas
Você pode usar o .NET Framework [biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) tipo para garantir que os recursos em suas bibliotecas de classe podem ser acessados em várias plataformas de projeto. Esse tipo de projeto está disponível no Visual Studio 2012 e tem como alvo o subconjunto portátil da biblioteca de classes do .NET Framework. Usar uma biblioteca de classes portátil garante que sua biblioteca pode ser acessada de aplicativos da área de trabalho, aplicativos do Silverlight, Windows Phone, e [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 O projeto de biblioteca de classes portátil faz apenas um subconjunto muito limitado dos tipos na <xref:System.Resources> namespace disponível para seu aplicativo, mas permitem que você use o <xref:System.Resources.ResourceManager> classe para recuperar recursos. No entanto, se estiver criando um aplicativo com o Visual Studio, você deverá usar o wrapper fortemente tipado criado pelo Visual Studio em vez de usar a classe <xref:System.Resources.ResourceManager> diretamente.

 Para criar um wrapper fortemente tipado no Visual Studio, defina o arquivo de recurso principal **modificador de acesso** no Visual Studio Resource Designer para **público**. Isso cria um arquivo [resourceFileName].designer.cs ou [resourceFileName].designer.vb que contém o wrapper ResourceManager fortemente tipado. Para obter mais informações sobre como usar um wrapper de recurso fortemente tipado, consulte a seção "Gerando uma classe fortemente tipada recursos" a [Resgen.exe (gerador de arquivo de recurso)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tópico.

## <a name="resource-manager-in-the-portable-class-library"></a>Gerenciador de recursos na biblioteca de classes portátil
 Em um projeto de biblioteca de classes portátil, todo o acesso aos recursos é tratado pelo <xref:System.Resources.ResourceManager> classe. Como tipos na <xref:System.Resources> namespace, como <xref:System.Resources.ResourceReader> e <xref:System.Resources.ResourceSet>, são não pode ser acessado de um projeto de biblioteca de classes portátil, eles não podem ser usados para acessar recursos.

 O projeto de biblioteca de classes portátil inclui os quatro <xref:System.Resources.ResourceManager> membros listados na tabela a seguir. Esses construtores e métodos permitem que você crie uma instância de um objeto <xref:System.Resources.ResourceManager> e recupere recursos de cadeia de caracteres.

|`ResourceManager` Membro|Descrição|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Cria uma instância de <xref:System.Resources.ResourceManager> para acessar o arquivo de recurso nomeado encontrado no assembly especificado.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Cria uma instância de <xref:System.Resources.ResourceManager> que corresponde ao tipo especificado.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Recupera um recurso nomeado para a cultura atual.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Recupera um recurso nomeado que pertence à cultura especificada.|

 A exclusão de outros <xref:System.Resources.ResourceManager> membros dos meios de biblioteca de classes portátil que serializados objetos, dados de não cadeia de caracteres e imagens não podem ser recuperados de um arquivo de recurso. Para usar recursos de uma biblioteca de classes portátil, você deve armazenar todos os dados de objeto na forma de cadeia de caracteres. Por exemplo, você pode armazenar valores numéricos em um arquivo de recurso convertendo-os em cadeias de caracteres, e pode recuperá-los e convertê-los novamente em números ao usar o método `Parse` ou `TryParse` do tipo de dados numéricos. Você pode converter imagens ou outros dados binários em uma representação de cadeia de caracteres ao chamar o método <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> e restaurá-los para uma matriz de bytes ao chamar o método <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-portable-class-library-and-windows-store-apps"></a>A biblioteca de classes portátil e aplicativos da Windows Store
 Projetos de biblioteca de classes portátil armazenam recursos em arquivos. resx, que são então compilados em arquivos. Resources e inseridos no assembly principal ou em assemblies satélites em tempo de compilação. Os aplicativos do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], por outro lado, exigem que os recursos sejam armazenados em arquivos .resw, que são compilados em um único arquivo de PRI (índice de recurso do pacote). No entanto, apesar dos formatos de arquivo incompatíveis, a biblioteca de classes portátil funcionará em um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo.

 Para consumir sua biblioteca de classes do aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], adicione uma referência a ela em seu projeto de aplicativo da Windows Store. Visual Studio transparentemente extrairá os recursos de seu assembly em um arquivo. resw e usá-lo para gerar um arquivo PRI do qual o tempo de execução do Windows poderá extrair recursos. Em tempo de execução, o tempo de execução do Windows executa o código em sua biblioteca de classes portátil, mas ele recupera os recursos da biblioteca de classes portátil do arquivo PRI.

 Se seu projeto de biblioteca de classes portátil incluir recursos localizados, você usa o modelo de hub e spoke para implantá-los como faria para uma biblioteca em um aplicativo da área de trabalho. Para consumir seu arquivo de recurso principal e quaisquer arquivos de recursos localizados em seu aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], adicione uma referência ao assembly principal. No tempo de compilação, o Visual Studio extrai os recursos do arquivo de recursos principal e quaisquer arquivos de recursos localizados em arquivos .resw separados. Em seguida, ele compila os arquivos. resw em um único arquivo PRI que acessa de tempo de execução do Windows em tempo de execução.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Exemplo: Biblioteca de classes portátil não localizado
 O exemplo seguinte da biblioteca de classes portátil simple, não localizado usa recursos para armazenar os nomes das colunas e para determinar o número de caracteres a serem reservados para dados tabulares. O exemplo usa um arquivo chamado LibResources.resx para armazenar os recursos de cadeia de caracteres listados na tabela a seguir.

|Nome do recurso|Valor do recurso|
|-------------------|--------------------|
|Born|Birthdate|
|BornLength|12|
|Hired|Hire Date|
|HiredLength|12|
|ID|ID|
|ID.Length|12|
|Nome|Nome|
|NameLength|25|
|Título|Employee Database|

 O código a seguir define uma `UILibrary` classe que usa o wrapper do Gerenciador de recursos chamado `resources` gerado pelo Visual Studio quando o **modificador de acesso** para o arquivo é alterado para **público** . A classe UILibrary analisa os dados de cadeia de caracteres conforme o necessário. . Observe que a classe está no namespace `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console. Ele requer uma referência a UILibrary a ser adicionado ao projeto de aplicativo de console.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Ele requer uma referência a UILibrary a ser adicionado ao projeto de aplicativo da Windows Store.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Exemplo: Biblioteca de classes portátil localizada
 O exemplo de biblioteca de classes portátil localizado inclui recursos para as culturas de inglês (Estados Unidos) e francês (França). A cultura do inglês (Estados Unidos) é a cultura do aplicativo padrão; seus recursos são mostrados na tabela a [seção anterior](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). O arquivo de recursos para francês (França) é chamado LibResources.fr-FR.resx e consiste nos recursos de cadeia de caracteres listados na tabela a seguir. O código-fonte para a classe `UILibrary` é o mesmo mostrado na seção anterior.

|Nome do recurso|Valor do recurso|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|ID|ID|
|Nome|Nom|
|Título|Base de données des employés|

 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console. Ele requer uma referência a UILibrary a ser adicionado ao projeto de aplicativo de console.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Ele requer uma referência a UILibrary a ser adicionado ao projeto de aplicativo da Windows Store. Usa a propriedade estática `ApplicationLanguages.PrimaryLanguageOverride` para definir o idioma preferencial do aplicativo como francês.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Resources.ResourceManager>
- [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
- [Empacotando e implantando recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
