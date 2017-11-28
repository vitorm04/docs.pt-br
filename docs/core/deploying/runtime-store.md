---
title: "Repositório de pacotes de tempo de execução"
description: "Este tópico explica o repositório de pacotes de tempo de execução e os manifestos de destino usados pelo .NET Core."
keywords: ".NET, .NET Core, dotnet store, repositório de pacotes de tempo de execução"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.openlocfilehash: 607f8259fa6d8488a7fccf3c7d90b6cf40d5f237
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-package-store"></a>Repositório de pacotes de tempo de execução

A partir do .NET Core 2.0, é possível empacotar e implantar aplicativos com relação a um conjunto conhecido de pacotes que existem no ambiente de destino. Os benefícios são implantações mais rápidas, menor uso de espaço em disco e desempenho aprimorado de inicialização em alguns casos.

Esse recurso é implementado como um *repositório de pacotes de tempo de execução*, que é um diretório em disco no qual os pacotes são armazenados (normalmente em */usr/local/share/dotnet/store* em macOS/Linux e *C:/Arquivos de Programas/dotnet/store* no Windows). Nesse diretório, há subdiretórios para arquiteturas e [estruturas de destino](../../standard/frameworks.md). O layout do arquivo é semelhante à maneira como os [ativos do NuGet são dispostos no disco](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

\dotnet   
&nbsp;&nbsp;\store   
&nbsp;&nbsp;&nbsp;&nbsp;\x64   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;\x86   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   

Um arquivo de *manifesto de destino* lista os pacotes no repositório de pacotes de tempo de execução. Os desenvolvedores podem direcionar esse manifesto ao publicar seu aplicativo. Normalmente, o manifesto de destino é fornecido pelo proprietário do ambiente de produção direcionado.

## <a name="preparing-a-runtime-environment"></a>Preparação de um ambiente de tempo de execução

O administrador de um ambiente de tempo de execução pode otimizar aplicativos para oferecer implantações mais rápidas e menor uso do espaço em disco criando um repositório de pacotes de tempo de execução e o manifesto de destino correspondente.

A primeira etapa é criar um *manifesto de repositório de pacotes* que lista os pacotes que compõem o repositório de pacotes de tempo de execução. Esse formato de arquivo é compatível com o formato de arquivo de projeto (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Exemplo**

O exemplo do manifesto do repositório de pacotes a seguir (*packages.csproj*) é usado para adicionar [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) e [`Moq`](https://www.nuget.org/packages/moq/) a um repositório de pacotes de tempo de execução:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Provisione o repositório de pacotes de tempo de execução executando `dotnet store` com o manifesto, tempo de execução e estrutura do repositório de pacotes:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Exemplo**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

É possível passar vários caminhos de manifesto do repositório de pacotes de destino para um único comando [`dotnet store`](../tools/dotnet-store.md) repetindo a opção e o caminho no comando.

Por padrão, a saída do comando é um repositório de pacotes no subdiretório *.dotnet/store* do perfil do usuário. É possível especificar um local diferente usando a opção `--output <OUTPUT_DIRECTORY>`. O diretório raiz do repositório contém um arquivo de manifesto de destino *artifact.xml*. Esse arquivo pode ser disponibilizado para download e ser usado por autores de aplicativos que desejam direcionar esse repositório durante a publicação.

**Exemplo**

O arquivo *artifact.xml* a seguir é produzido depois de executar o exemplo anterior. Observe que [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) é uma dependência de `Moq`, portanto, está incluído automaticamente e é exibido no arquivo de manifesto *artifacts.xml*.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publicação de um aplicativo em um manifesto de destino

Se você tiver um arquivo de manifesto de destino em disco, especifique o caminho para o arquivo ao publicar seu aplicativo com o comando [`dotnet publish`](../tools/dotnet-publish.md):

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Exemplo**

```console
dotnet publish --manifest manifest.xml
```

Implante o aplicativo publicado resultante em um ambiente que tem os pacotes descritos no manifesto de destino. Se isso não for feito, o aplicativo falhará ao iniciar.

Especifique vários manifestos de destino ao publicar um aplicativo, repetindo a opção e o caminho (por exemplo, `--manifest manifest1.xml --manifest manifest2.xml`). Quando você fizer isso, o aplicativo será cortado para a união de pacotes especificada nos arquivos de manifesto de destino fornecidos para o comando.

## <a name="specifying-target-manifests-in-the-project-file"></a>Especificação de manifestos de destino no arquivo de projeto

Uma alternativa para especificar os manifestos de destino com o comando [`dotnet publish`](../tools/dotnet-publish.md) é especificá-los no arquivo de projeto como uma lista de caminhos separados por ponto-e-vírgula em uma marga **\<TargetManifestFiles>**.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Especifique os manifestos de destino no arquivo de projeto somente quando o ambiente de destino para o aplicativo for bem conhecido, como para projetos .NET Core. Esse não é o caso para projetos de software livre. Normalmente, os usuários de um projeto de software livre o implantam em diferentes ambientes de produção. Geralmente, esses ambientes de produção têm diferentes conjuntos de pacotes pré-instalados. Não é possível fazer suposições sobre o manifesto de destino nesses ambientes, então você deve usar a opção `--manifest` de [`dotnet publish`](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>Repositório implícito do ASP.NET Core

O recurso do repositório de pacotes de tempo de execução é usado implicitamente por um aplicativo ASP.NET Core quando o aplicativo é implantado como um aplicativo [FDD (implantação dependente da estrutura)](index.md#framework-dependent-deployments-fdd). Os destinos em [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) incluem manifestos que referenciam o repositório de pacotes implícito no sistema de destino. Além disso, qualquer aplicativo FDD que dependa do pacote `Microsoft.AspNetCore.All` resulta em um aplicativo publicado que contém apenas o aplicativo e seus ativos e não os pacotes listados no metapackage `Microsoft.AspNetCore.All`. Pressupõe-se que esses pacotes estão presentes no sistema de destino.

O repositório de pacotes de tempo de execução é instalado no host quando o SDK de .NET Core é instalado. Talvez outros instaladores forneçam o repositório de pacotes de tempo de execução, incluindo instalações Zip/tarball do SDK do .NET Core, `apt-get`, Red Hat Yum, o pacote de hospedagem do Windows Server do .NET Core e instalações manuais de repositório de pacotes de tempo de execução.

Ao implantar um aplicativo [FDD (dependente da estrutura de implantação)](index.md#framework-dependent-deployments-fdd), certifique-se de que o ambiente de destino tem o SDK do .NET Core instalado. Se o aplicativo for implantado em um ambiente que não inclui o ASP.NET Core, será possível recusar o repositório implícito especificando o conjunto **\<PublishWithAspNetCoreTargetManifest>** definido como `false` no arquivo de projeto como no exemplo a seguir:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> Para aplicativos [SCD (implantação autocontida)](index.md#self-contained-deployments-scd), pressupõe-se que o sistema de destino não contenha necessariamente os pacotes de manifesto necessários. Portanto, **\<PublishWithAspNetCoreTargetManifest>** não pode ser definido como `true` para um aplicativo SCD.

Se você implantar um aplicativo com uma dependência de manifesto presente na implantação (o assembly está presente na pasta *bin*), o repositório de pacotes de tempo de execução *não será usado* no host desse assembly. O assembly da pasta *bin* é usado, independentemente de sua presença no repositório de pacotes de tempo de execução no host.

A versão da dependência indicada no manifesto deve corresponder à versão da dependência no repositório de pacotes de tempo de execução. Se você tiver uma incompatibilidade de versão entre a dependência no manifesto de destino e a versão que existe no repositório de pacotes de tempo de execução e o aplicativo não incluir a versão necessária do pacote em sua implantação, a inicialização do aplicativo falhará. A exceção inclui o nome do manifesto de destino chamado que chamou o assembly do repositório de pacotes de tempo de execução, que ajuda você a solucionar problemas de incompatibilidade.

Quando a implantação é *cortada* na publicação, somente as versões específicas dos pacotes de manifesto indicadas são retidas na saída publicada. Os pacotes nas versões indicadas devem estar presentes no host do aplicativo a ser iniciado.

## <a name="see-also"></a>Consulte também
 [dotnet-publish](../tools/dotnet-publish.md)  
 [dotnet-store](../tools/dotnet-store.md)  
