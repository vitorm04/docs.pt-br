---
title: Criar um novo projeto ASP.NET Core gRPC-gRPC para desenvolvedores do WCF
description: Saiba como criar um projeto do gRPC usando o Visual Studio ou a linha de comando.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a30d19e1e48692ad68a648406d4bf369937744d7
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846717"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Criar um projeto ASP.NET Core gRPC

O .NET Core vem com uma poderosa ferramenta CLI, `dotnet`, que permite criar e gerenciar projetos e soluções na linha de comando. A ferramenta está intimamente integrada ao Visual Studio, de modo que tudo também está disponível por meio da interface GUI familiar. Este capítulo mostrará as duas maneiras de criar um novo projeto ASP.NET Core gRPC: primeiro com o Visual Studio e, em seguida, com o CLI do .NET Core.

## <a name="create-the-project-using-visual-studio"></a>Criar o projeto usando o Visual Studio

> [!IMPORTANT]
> Para desenvolver qualquer aplicativo ASP.NET Core 3,0, você precisa do Visual Studio 2019,3 ou posterior com a ASP.NET e a carga de trabalho de **desenvolvimento Web** instaladas.

Crie uma solução vazia chamada **Traders** a partir do modelo de *solução em branco* . Adicione uma pasta de solução chamada `src`, clique com o botão direito do mouse na pasta e escolha **adicionar** > **novo projeto** no menu de contexto. Insira `grpc` na caixa de pesquisa de modelo e você deverá ver um modelo de projeto chamado `gRPC Service`.

![Caixa de diálogo Adicionar novo projeto mostrando o modelo de projeto do serviço gRPC](media/create-project/new-grpc-project.png)

Clique em **Avançar** para continuar na caixa de diálogo **Configurar projeto** e nomeie o projeto `TraderSys.Portfolios`e adicione um subdiretório `src` ao **local**.

![Caixa de diálogo Configurar projeto](media/create-project/configure-project.png)

Clique em **Avançar** para ir para a caixa de diálogo **novo projeto gRPC** .

![Caixa de diálogo novo projeto gRPC](media/create-project/create-new-grpc-service.png)

No momento, há opções limitadas para a criação do serviço. O Docker será introduzido posteriormente no livro, portanto, deixe essa caixa de seleção desmarcada por enquanto e clique em **criar**. Seu primeiro projeto ASP.NET Core gRPC 3,0 é gerado e adicionado à solução. Se você não quiser saber sobre como trabalhar com o `dotnet CLI`, pule para a seção [limpar o código de exemplo](#clean-up-the-example-code) .

## <a name="create-the-project-using-the-net-core-cli"></a>Criar o projeto usando o CLI do .NET Core

Esta seção aborda a criação de soluções e projetos da linha de comando.

Crie a solução, conforme mostrado abaixo. O sinalizador `-o` (ou `--output`) especifica o diretório de saída, que será criado no diretório atual se ele não existir. A solução receberá o mesmo nome que o diretório, ou seja, `TraderSys.sln`. Você pode fornecer um nome diferente usando o sinalizador `-n` (ou `--name`).

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 vem com um modelo de CLI para serviços gRPCs. Crie o novo projeto usando este modelo, colocando-o em um subdiretório `src` como é a Convenção para projetos ASP.NET Core. O projeto será nomeado após o diretório (ou seja, `TraderSys.Portfolios.csproj`), a menos que você especifique um nome diferente com o sinalizador `-n`.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Por fim, adicione o projeto à solução usando o comando `dotnet sln`.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Como o diretório fornecido contém apenas um único arquivo de `.csproj`, você pode sair com a especificação apenas do diretório para salvar a digitação.

Agora você pode abrir essa solução no Visual Studio 2019, Visual Studio Code ou em qualquer editor que preferir.

## <a name="clean-up-the-example-code"></a>Limpar o código de exemplo

Agora você criou um serviço de exemplo usando o modelo gRPC, que foi revisado anteriormente no livro. Isso não é útil em nosso contexto de comércio de ações, portanto, vamos editar as coisas para nosso primeiro projeto.

### <a name="rename-and-edit-the-proto-file"></a>Renomear e editar o arquivo proto

Vá em frente e renomeie o arquivo de `Protos/greet.proto` para `Protos/portfolios.proto` e abra-o em seu editor. Exclua tudo depois da linha de `package`, altere os nomes `option csharp_namespace`, `package` e `service` e remova o serviço de `SayHello` padrão, para que o código tenha esta aparência.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> O modelo não adiciona a parte de namespace `Protos` por padrão, mas adicioná-la torna mais fácil manter classes gRPC e suas próprias classes claramente separadas em seu código.

Se você renomear o arquivo de `greet.proto` em um ambiente de desenvolvimento integrado (IDE) como o Visual Studio, uma referência a esse arquivo será atualizada automaticamente no arquivo de `.csproj`. Mas, em algum outro editor, como Visual Studio Code, essa referência não é atualizada automaticamente, portanto, você precisa editar o arquivo de projeto manualmente.

No gRPC Build targets, há um elemento `Protobuf` item que permite especificar quais `.proto` arquivos devem ser compilados e qual forma de geração de código é necessária (ou seja, "Server" ou "Client").

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Renomeie a classe GreeterService

A classe `GreeterService` está na pasta `Services` e herda de `Greeter.GreeterBase`. Renomeie-o para `PortfolioService` e altere a classe base para `Portfolios.PortfoliosBase`. Exclua os métodos de `override`.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Houve uma referência à classe `GreeterService` no método `Configure` na classe `Startup`. Se você usou a refatoração para renomear a classe, essa referência deverá ter sido atualizada automaticamente. No entanto, se você não tiver, precisará editá-lo manualmente.

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

Na próxima seção, adicionaremos funcionalidade a esse novo serviço.

>[!div class="step-by-step"]
>[Anterior](migrate-wcf-to-grpc.md)
>[Próximo](migrate-request-reply.md)
