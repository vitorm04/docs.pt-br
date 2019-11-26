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
ms.openlocfilehash: b32c2e354ea48e25ddb0aa561eb576cbfd89e3fb
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204748"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Recursos do aplicativo para bibliotecas direcionadas a várias plataformas
You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) project type to ensure that resources in your class libraries can be accessed from multiple platforms. This project type is available in Visual Studio 2012 and targets the portable subset of the .NET Framework class library. Using  a Portable Class Library ensures that your library can be accessed from desktop apps, Silverlight apps, Windows Phone apps, and Windows 8.x Store apps.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 The Portable Class Library project makes only a very limited subset of the types in the <xref:System.Resources> namespace available to your application, but it does allow you to use the <xref:System.Resources.ResourceManager> class to retrieve resources. No entanto, se estiver criando um aplicativo com o Visual Studio, você deverá usar o wrapper fortemente tipado criado pelo Visual Studio em vez de usar a classe <xref:System.Resources.ResourceManager> diretamente.

 To create a strongly typed wrapper in Visual Studio, set the main resource file's **Access Modifier** in the Visual Studio Resource Designer to **Public**. Isso cria um arquivo [resourceFileName].designer.cs ou [resourceFileName].designer.vb que contém o wrapper ResourceManager fortemente tipado. For more information about using a strongly typed resource wrapper, see the "Generating a Strongly Typed Resource Class" section in the [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) topic.

## <a name="resource-manager-in-the-portable-class-library"></a>Resource Manager in the Portable Class Library
 In a Portable Class Library project, all access to resources is handled by the <xref:System.Resources.ResourceManager> class. Because types in the <xref:System.Resources> namespace, such as <xref:System.Resources.ResourceReader> and <xref:System.Resources.ResourceSet>, are not accessible from a Portable Class Library project, they cannot be used to access resources.

 The Portable Class Library project includes the four <xref:System.Resources.ResourceManager> members listed in the following table. Esses construtores e métodos permitem que você crie uma instância de um objeto <xref:System.Resources.ResourceManager> e recupere recursos de cadeia de caracteres.

|Membro do `ResourceManager`|Descrição|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Cria uma instância de <xref:System.Resources.ResourceManager> para acessar o arquivo de recurso nomeado encontrado no assembly especificado.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Cria uma instância de <xref:System.Resources.ResourceManager> que corresponde ao tipo especificado.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Recupera um recurso nomeado para a cultura atual.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Recupera um recurso nomeado que pertence à cultura especificada.|

 The exclusion of other <xref:System.Resources.ResourceManager> members from the Portable Class Library means that serialized objects, non-string data, and images cannot be retrieved from a resource file. To use resources from a Portable Class Library, you should store all  object data in string form. Por exemplo, você pode armazenar valores numéricos em um arquivo de recurso convertendo-os em cadeias de caracteres, e pode recuperá-los e convertê-los novamente em números ao usar o método `Parse` ou `TryParse` do tipo de dados numéricos. Você pode converter imagens ou outros dados binários em uma representação de cadeia de caracteres ao chamar o método <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> e restaurá-los para uma matriz de bytes ao chamar o método <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-portable-class-library-and-windows-store-apps"></a>The Portable Class Library and Windows Store Apps
 Portable Class Library projects store resources in .resx files, which are then compiled into .resources files and embedded in the main assembly or in satellite assemblies at compile time. Windows 8.x Store apps, on the other hand, require resources to be stored in .resw files, which are then compiled into a single package resource index (PRI) file. However, despite the incompatible file formats, your Portable Class Library will work in a Windows 8.x Store app.

 To consume your class library from a Windows 8.x Store app, add a reference to it in your Windows Store app project. Visual Studio will transparently extract the resources from your assembly into a .resw file and use it to generate a PRI file from which the Windows Runtime can extract resources. At run time, the Windows Runtime executes the code in your Portable Class Library, but it retrieves your Portable Class Library's resources from the PRI file.

 If your Portable Class Library project includes localized resources, you use the hub-and-spoke model to deploy them just as you would for a library in a desktop app. To consume your main resource file and any localized resource files in your Windows 8.x Store app, you add a reference to the main assembly. No tempo de compilação, o Visual Studio extrai os recursos do arquivo de recursos principal e quaisquer arquivos de recursos localizados em arquivos .resw separados. It then compiles the .resw files into a single PRI file that the Windows Runtime accesses at run time.

<a name="NonLoc"></a>
## <a name="example-non-localized-portable-class-library"></a>Example: Non-Localized Portable Class Library
 The following simple, non-localized Portable Class Library example uses resources to store the names of columns and to determine the number of characters to reserve for tabular data. O exemplo usa um arquivo chamado LibResources.resx para armazenar os recursos de cadeia de caracteres listados na tabela a seguir.

|Nome do recurso|Valor do recurso|
|-------------------|--------------------|
|Born|Birthdate|
|BornLength|12|
|Hired|Hire Date|
|HiredLength|12|
|ID|ID|
|ID.Length|12|
|Name|Name|
|NameLength|25|
|Título|Employee Database|

 The following code defines a `UILibrary` class that uses the Resource Manager wrapper named `resources` generated by Visual Studio when the **Access Modifier** for the file is changed to **Public**. A classe UILibrary analisa os dados de cadeia de caracteres conforme o necessário. . Observe que a classe está no namespace `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console. It requires a reference to UILibrary.dll to be added to the console app project.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 The following code illustrates how the `UILibrary` class and its resources can be accessed from a Windows 8.x Store app. It requires a reference to UILibrary.dll to be added to the Windows Store app project.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Example: Localized Portable Class Library
 The following localized Portable Class Library example includes resources for the French (France) and English (United States) cultures. The English (United States) culture is the app's default culture; its resources are shown in the table in the [previous section](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). O arquivo de recursos para francês (França) é chamado LibResources.fr-FR.resx e consiste nos recursos de cadeia de caracteres listados na tabela a seguir. O código-fonte para a classe `UILibrary` é o mesmo mostrado na seção anterior.

|Nome do recurso|Valor do recurso|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|ID|ID|
|Name|Nom|
|Título|Base de données des employés|

 O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console. It requires a reference to UILibrary.dll to be added to the console app project.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 The following code illustrates how the `UILibrary` class and its resources can be accessed from a Windows 8.x Store app. It requires a reference to UILibrary.dll to be added to the Windows Store app project. Usa a propriedade estática `ApplicationLanguages.PrimaryLanguageOverride` para definir o idioma preferencial do aplicativo como francês.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Resources.ResourceManager>
- [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
- [Empacotando e implantando recursos](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
