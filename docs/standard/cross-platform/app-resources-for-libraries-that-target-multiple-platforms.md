---
title: Recursos do aplicativo para bibliotecas direcionadas a várias plataformas
ms.date: 03/30/2017
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
ms.openlocfilehash: f4682b9ffcb0edb4e54c427968c3d40c0de134d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Recursos do aplicativo para bibliotecas direcionadas a várias plataformas
Você pode usar o .NET Framework [biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) tipo para garantir que os recursos em suas bibliotecas de classe podem ser acessados em várias plataformas de projeto. Esse tipo de projeto está disponível em [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] e tem como alvo o subconjunto portátil da biblioteca de classes do .NET Framework. Usar um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] garante que a biblioteca possa ser acessada de aplicativos da área de trabalho, Silverlight, Windows Phone e [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
 O projeto [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] disponibiliza somente um subconjunto muito limitado dos tipos no namespace <xref:System.Resources> para o seu aplicativo, mas permite que você use a classe <xref:System.Resources.ResourceManager> para recuperar recursos. No entanto, se estiver criando um aplicativo com o Visual Studio, você deverá usar o wrapper fortemente tipado criado pelo Visual Studio em vez de usar a classe <xref:System.Resources.ResourceManager> diretamente.  
  
 Para criar um wrapper com rigidez de tipos no Visual Studio, defina o arquivo de recurso principal **modificador de acesso** no Designer de recursos Visual Studio para **público**. Isso cria um arquivo [resourceFileName].designer.cs ou [resourceFileName].designer.vb que contém o wrapper ResourceManager fortemente tipado. Para obter mais informações sobre como usar um wrapper de recursos fortemente tipados, consulte a seção "Gerar um fortemente tipado classe de recurso" a [Resgen.exe (gerador de arquivo)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tópico.  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a>Gerenciador de Recursos no [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Em um projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], todos os acessos a recursos são tratados pela classe <xref:System.Resources.ResourceManager>. Como tipos no namespace <xref:System.Resources>, como <xref:System.Resources.ResourceReader> e <xref:System.Resources.ResourceSet>, não são acessíveis a partir de um projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], eles não podem ser usados para acessar recursos.  
  
 O projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] inclui os quatro membros <xref:System.Resources.ResourceManager> listados na tabela a seguir. Esses construtores e métodos permitem que você crie uma instância de um objeto <xref:System.Resources.ResourceManager> e recupere recursos de cadeia de caracteres.  
  
|Membro do `ResourceManager`|Descrição|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Cria uma instância de <xref:System.Resources.ResourceManager> para acessar o arquivo de recurso nomeado encontrado no assembly especificado.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Cria uma instância de <xref:System.Resources.ResourceManager> que corresponde ao tipo especificado.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Recupera um recurso nomeado para a cultura atual.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Recupera um recurso nomeado que pertence à cultura especificada.|  
  
 A exclusão de outros membros de <xref:System.Resources.ResourceManager> do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] significa que objetos serializados, dados que não sejam cadeia de caracteres, e imagens não podem ser recuperados de um arquivo de recurso. Para usar recursos de um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], você deve armazenar todos os dados de objeto na forma de cadeia de caracteres. Por exemplo, você pode armazenar valores numéricos em um arquivo de recurso convertendo-os em cadeias de caracteres, e pode recuperá-los e convertê-los novamente em números ao usar o método `Parse` ou `TryParse` do tipo de dados numéricos. Você pode converter imagens ou outros dados binários em uma representação de cadeia de caracteres ao chamar o método <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> e restaurá-los para uma matriz de bytes ao chamar o método <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a>Os aplicativos do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] e da Windows Store  
 Projetos do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] armazenam recursos em arquivos .resx que são compilados em arquivos .resources e inseridos no assembly principal ou em assemblies satélites em tempo de compilação. Os aplicativos do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], por outro lado, exigem que os recursos sejam armazenados em arquivos .resw, que são compilados em um único arquivo de PRI (índice de recurso do pacote). No entanto, independentemente dos formatos de arquivo incompatíveis, seu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] funcionará em um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
 Para consumir sua biblioteca de classes do aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], adicione uma referência a ela em seu projeto de aplicativo da Windows Store. O Visual Studio extrairá de forma transparente os recursos de seu assembly em um arquivo .resw e os usará para gerar um arquivo de PRI do qual o [!INCLUDE[wrt](../../../includes/wrt-md.md)] poderá extrair recursos. No tempo de execução, o [!INCLUDE[wrt](../../../includes/wrt-md.md)] executa o código em seu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], mas recupera recursos de sua Biblioteca de Classes Portátil do arquivo de PRI.  
  
 Se seu projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] incluir recursos localizados, use o modelo hub e spoke para implantá-los exatamente como faria para uma biblioteca em um aplicativo da área de trabalho. Para consumir seu arquivo de recurso principal e quaisquer arquivos de recursos localizados em seu aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], adicione uma referência ao assembly principal. No tempo de compilação, o Visual Studio extrai os recursos do arquivo de recursos principal e quaisquer arquivos de recursos localizados em arquivos .resw separados. Em seguida, ele cria os arquivos .resw em um único arquivo de PRI que acessa o [!INCLUDE[wrt](../../../includes/wrt-md.md)] em tempo de execução.  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a>Exemplo: [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] não localizado  
 O exemplo simples e não localizado do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] a seguir usa recursos para armazenar os nomes das colunas e determinar o número de caracteres a serem reservados para dados tabulares. O exemplo usa um arquivo chamado LibResources.resx para armazenar os recursos de cadeia de caracteres listados na tabela a seguir.  
  
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
  
 O código a seguir define uma `UILibrary` classe que usa o wrapper do Gerenciador de recursos denominado `resources` gerado pelo Visual Studio quando o **modificador de acesso** para o arquivo é alterado para **público** . A classe UILibrary analisa os dados de cadeia de caracteres conforme o necessário. . Observe que a classe está no namespace `MyCompany.Employees`.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console. Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo de console.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo da Windows Store.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a>Exemplo: [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localizado  
 O exemplo do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localizado a seguir inclui recursos para francês (França) e inglês (Estados Unidos). A cultura do inglês (Estados Unidos) é a cultura padrão do aplicativo seus recursos são mostrados na tabela de [seção anterior](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). O arquivo de recursos para francês (França) é chamado LibResources.fr-FR.resx e consiste nos recursos de cadeia de caracteres listados na tabela a seguir. O código-fonte para a classe `UILibrary` é o mesmo mostrado na seção anterior.  
  
|Nome do recurso|Valor do recurso|  
|-------------------|--------------------|  
|Born|Date de naissance|  
|BornLength|20|  
|Hired|Date embauché|  
|HiredLength|16|  
|ID|ID|  
|Nome|Nom|  
|Título|Base de données des employés|  
  
 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console. Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo de console.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo da Windows Store. Usa a propriedade estática `ApplicationLanguages.PrimaryLanguageOverride` para definir o idioma preferencial do aplicativo como francês.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Resources.ResourceManager>  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)  
 [Empacotando e implantando recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
