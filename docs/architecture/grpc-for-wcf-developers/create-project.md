---
title: Criar um novo projeto ASP.NET Core gRPC-gRPC para desenvolvedores do WCF
description: Saiba como criar um projeto do gRPC usando o Visual Studio ou a linha de comando.
ms.date: 09/02/2019
ms.openlocfilehash: 992c3f57be25ae2517d41437170dc287f58934b6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967889"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="e288e-103">Criar um projeto ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="e288e-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="e288e-104">O .NET Core vem com uma poderosa ferramenta CLI, `dotnet`, que permite criar e gerenciar projetos e soluções na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e288e-104">.NET Core comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="e288e-105">A ferramenta está intimamente integrada ao Visual Studio, de modo que tudo também está disponível por meio da interface GUI familiar.</span><span class="sxs-lookup"><span data-stu-id="e288e-105">The tool is closely integrated with Visual Studio, so everything is also available through the familiar GUI interface.</span></span> <span data-ttu-id="e288e-106">Este capítulo mostrará as duas maneiras de criar um novo projeto ASP.NET Core gRPC: primeiro com o Visual Studio e, em seguida, com o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e288e-106">This chapter will show both ways to create a new ASP.NET Core gRPC project: first with Visual Studio, then with the .NET Core CLI.</span></span>

## <a name="create-the-project-using-visual-studio"></a><span data-ttu-id="e288e-107">Criar o projeto usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e288e-107">Create the project using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e288e-108">Para desenvolver qualquer aplicativo ASP.NET Core 3,0, você precisa do Visual Studio 2019,3 ou posterior com a ASP.NET e a carga de trabalho de **desenvolvimento Web** instaladas.</span><span class="sxs-lookup"><span data-stu-id="e288e-108">To develop any ASP.NET Core 3.0 app, you need Visual Studio 2019.3 or later with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="e288e-109">Crie uma solução vazia chamada **Traders** a partir do modelo de *solução em branco* .</span><span class="sxs-lookup"><span data-stu-id="e288e-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="e288e-110">Adicione uma pasta de solução chamada `src`, clique com o botão direito do mouse na pasta e escolha **adicionar** > **novo projeto** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="e288e-110">Add a Solution Folder called `src`, then right-click on the folder and choose **Add** > **New Project** from the context menu.</span></span> <span data-ttu-id="e288e-111">Insira `grpc` na caixa de pesquisa de modelo e você deverá ver um modelo de projeto chamado `gRPC Service`.</span><span class="sxs-lookup"><span data-stu-id="e288e-111">Enter `grpc` in the template search box and you should see a project template called `gRPC Service`.</span></span>

![Caixa de diálogo Adicionar novo projeto mostrando o modelo de projeto do serviço gRPC](media/create-project/new-grpc-project.png)

<span data-ttu-id="e288e-113">Clique em **Avançar** para continuar na caixa de diálogo **Configurar projeto** e nomeie o projeto `TraderSys.Portfolios`e adicione um subdiretório `src` ao **local**.</span><span class="sxs-lookup"><span data-stu-id="e288e-113">Click **Next** to continue to the **Configure project** dialog and name the project `TraderSys.Portfolios`, and add an `src` subdirectory to the **Location**.</span></span>

![Caixa de diálogo Configurar projeto](media/create-project/configure-project.png)

<span data-ttu-id="e288e-115">Clique em **Avançar** para ir para a caixa de diálogo **novo projeto gRPC** .</span><span class="sxs-lookup"><span data-stu-id="e288e-115">Click **Next** to continue to the **New gRPC project** dialog.</span></span>

![Caixa de diálogo novo projeto gRPC](media/create-project/create-new-grpc-service.png)

<span data-ttu-id="e288e-117">No momento, há opções limitadas para a criação do serviço.</span><span class="sxs-lookup"><span data-stu-id="e288e-117">At present, there are limited options for the service creation.</span></span> <span data-ttu-id="e288e-118">O Docker será introduzido posteriormente no livro, portanto, deixe essa caixa de seleção desmarcada por enquanto e clique em **criar**.</span><span class="sxs-lookup"><span data-stu-id="e288e-118">Docker will be introduced later in the book, so leave that checkbox unchecked for now and just click **Create**.</span></span> <span data-ttu-id="e288e-119">Seu primeiro projeto ASP.NET Core gRPC 3,0 é gerado e adicionado à solução.</span><span class="sxs-lookup"><span data-stu-id="e288e-119">Your first ASP.NET Core 3.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="e288e-120">Se você não quiser saber sobre como trabalhar com o `dotnet CLI`, pule para a seção [limpar o código de exemplo](#clean-up-the-example-code) .</span><span class="sxs-lookup"><span data-stu-id="e288e-120">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-using-the-net-core-cli"></a><span data-ttu-id="e288e-121">Criar o projeto usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e288e-121">Create the project using the .NET Core CLI</span></span>

<span data-ttu-id="e288e-122">Esta seção aborda a criação de soluções e projetos da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e288e-122">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="e288e-123">Crie a solução, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="e288e-123">Create the solution as shown below.</span></span> <span data-ttu-id="e288e-124">O sinalizador `-o` (ou `--output`) especifica o diretório de saída, que será criado no diretório atual se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="e288e-124">The `-o` (or `--output`) flag specifies the output directory, which will be created in the current directory if it does not exist.</span></span> <span data-ttu-id="e288e-125">A solução receberá o mesmo nome que o diretório, ou seja, `TraderSys.sln`. Você pode fornecer um nome diferente usando o sinalizador `-n` (ou `--name`).</span><span class="sxs-lookup"><span data-stu-id="e288e-125">The solution will be given the same name as the directory, i.e. `TraderSys.sln`. You can provide a different name using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="e288e-126">ASP.NET Core 3,0 vem com um modelo de CLI para serviços gRPCs.</span><span class="sxs-lookup"><span data-stu-id="e288e-126">ASP.NET Core 3.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="e288e-127">Crie o novo projeto usando este modelo, colocando-o em um subdiretório `src` como é a Convenção para projetos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e288e-127">Create the new project using this template, putting it into an `src` subdirectory as is the convention for ASP.NET Core projects.</span></span> <span data-ttu-id="e288e-128">O projeto será nomeado após o diretório (ou seja, `TraderSys.Portfolios.csproj`), a menos que você especifique um nome diferente com o sinalizador `-n`.</span><span class="sxs-lookup"><span data-stu-id="e288e-128">The project will be named after the directory (i.e. `TraderSys.Portfolios.csproj`) unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="e288e-129">Por fim, adicione o projeto à solução usando o comando `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="e288e-129">Finally, add the project to the solution using the `dotnet sln` command.</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="e288e-130">Como o diretório fornecido contém apenas um único arquivo de `.csproj`, você pode sair com a especificação apenas do diretório para salvar a digitação.</span><span class="sxs-lookup"><span data-stu-id="e288e-130">Since the given directory only contains a single `.csproj` file, you can get away with specifying just the directory to save typing.</span></span>

<span data-ttu-id="e288e-131">Agora você pode abrir essa solução no Visual Studio 2019, Visual Studio Code ou em qualquer editor que preferir.</span><span class="sxs-lookup"><span data-stu-id="e288e-131">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="e288e-132">Limpar o código de exemplo</span><span class="sxs-lookup"><span data-stu-id="e288e-132">Clean up the example code</span></span>

<span data-ttu-id="e288e-133">Agora você criou um serviço de exemplo usando o modelo gRPC, que foi revisado anteriormente no livro.</span><span class="sxs-lookup"><span data-stu-id="e288e-133">You've now created an example service using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="e288e-134">Isso não é útil em nosso contexto de comércio de ações, portanto, vamos editar as coisas para nosso primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="e288e-134">This isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="e288e-135">Renomear e editar o arquivo proto</span><span class="sxs-lookup"><span data-stu-id="e288e-135">Rename and edit the proto file</span></span>

<span data-ttu-id="e288e-136">Vá em frente e renomeie o arquivo de `Protos/greet.proto` para `Protos/portfolios.proto` e abra-o em seu editor.</span><span class="sxs-lookup"><span data-stu-id="e288e-136">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto` and open it in your editor.</span></span> <span data-ttu-id="e288e-137">Exclua tudo depois da linha de `package`, altere os nomes `option csharp_namespace`, `package` e `service` e remova o serviço de `SayHello` padrão, para que o código tenha esta aparência.</span><span class="sxs-lookup"><span data-stu-id="e288e-137">Delete everything after the `package` line, then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service, so the code looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="e288e-138">O modelo não adiciona a parte de namespace `Protos` por padrão, mas adicioná-la torna mais fácil manter classes gRPC e suas próprias classes claramente separadas em seu código.</span><span class="sxs-lookup"><span data-stu-id="e288e-138">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="e288e-139">Se você renomear o arquivo de `greet.proto` em um ambiente de desenvolvimento integrado (IDE) como o Visual Studio, uma referência a esse arquivo será atualizada automaticamente no arquivo de `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="e288e-139">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="e288e-140">Mas, em algum outro editor, como Visual Studio Code, essa referência não é atualizada automaticamente, portanto, você precisa editar o arquivo de projeto manualmente.</span><span class="sxs-lookup"><span data-stu-id="e288e-140">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="e288e-141">No gRPC Build targets, há um elemento `Protobuf` item que permite especificar quais `.proto` arquivos devem ser compilados e qual forma de geração de código é necessária (ou seja, "Server" ou "Client").</span><span class="sxs-lookup"><span data-stu-id="e288e-141">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="e288e-142">Renomeie a classe GreeterService</span><span class="sxs-lookup"><span data-stu-id="e288e-142">Rename the GreeterService class</span></span>

<span data-ttu-id="e288e-143">A classe `GreeterService` está na pasta `Services` e herda de `Greeter.GreeterBase`.</span><span class="sxs-lookup"><span data-stu-id="e288e-143">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="e288e-144">Renomeie-o para `PortfolioService` e altere a classe base para `Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="e288e-144">Rename it to `PortfolioService` and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="e288e-145">Exclua os métodos de `override`.</span><span class="sxs-lookup"><span data-stu-id="e288e-145">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="e288e-146">Houve uma referência à classe `GreeterService` no método `Configure` na classe `Startup`.</span><span class="sxs-lookup"><span data-stu-id="e288e-146">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="e288e-147">Se você usou a refatoração para renomear a classe, essa referência deverá ter sido atualizada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e288e-147">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="e288e-148">No entanto, se você não tiver, precisará editá-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="e288e-148">However, if you didn't, you need to edit it manually.</span></span>

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

<span data-ttu-id="e288e-149">Na próxima seção, adicionaremos funcionalidade a esse novo serviço.</span><span class="sxs-lookup"><span data-stu-id="e288e-149">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e288e-150">[Anterior](migrate-wcf-to-grpc.md)
>[Próximo](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="e288e-150">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
