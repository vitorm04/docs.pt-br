---
title: "Instruções passo a passo - acessando um serviço Web por meio de provedores de tipos (F #)"
description: "Saiba como usar o provedor de tipo WSDL Web Services Description Language (), disponível no F # 3.0 para acessar um serviço em WSDL."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>Instruções passo a passo: acessando um serviço Web por meio de provedores de tipos

> [!NOTE]
Este guia foi escrito para F # 3.0 e será atualizado.  Consulte [FSharp.Data](http://fsharp.github.io/FSharp.Data/) para provedores de tipo de plataforma cruzada atualizados.

> [!NOTE]
Os links de referência de API levará você para o MSDN.  A referência da API docs.microsoft.com não está completa.

Este passo a passo mostra como usar o provedor de tipos de WSDL Web Services Description Language () está disponível em F # 3.0 para acessar um serviço em WSDL. Em outras linguagens .NET, gerar o código para acessar o serviço web por chamada svcutil.exe ou adicionando uma referência da web no, por exemplo, um c# do projeto para obter o Visual Studio para chamar o svcutil.exe para você. Em F #, você tem a opção adicional de usar o provedor de tipo WSDL, portanto, assim que você escreva o código que cria o tipo WsdlService, os tipos são gerados e ficam disponíveis. Esse processo depende do serviço está disponível quando você estiver escrevendo o código.

Esta explicação passo a passo mostra as seguintes tarefas. Você deve concluir-os nesta ordem para a passo a passo para ter êxito:


- Criando o projeto
<br />

- Configurando o provedor de tipos
<br />

- Chamar o serviço web e processar os resultados
<br />


## <a name="creating-the-project"></a>Criando o projeto
Na etapa, você pode cria um projeto e adicionar as referências apropriadas para usar um provedor de tipo WSDL.


#### <a name="to-create-and-set-up-an-f-project"></a>Para criar e configurar um projeto de F#

1. Abra um novo projeto de aplicativo de Console em F #.
<br />

2. Em **Solution Explorer**, abra o menu de atalho para o projeto **referência** nó e, em seguida, escolha **adicionar referência**.
<br />

3. No **Assemblies** área, escolha **Framework**e, em seguida, na lista de assemblies disponíveis, escolha **Serialization** e  **System. ServiceModel**.
<br />

4. No **Assemblies** área, escolha **extensões**.
<br />

5. Na lista de assemblies disponíveis, escolha **FSharp.Data.TypeProviders**e, em seguida, escolha o **Okey** botão para adicionar referências a esses assemblies.
<br />

## <a name="configuring-the-type-provider"></a>Configurando o provedor de tipos
Nesta etapa, você pode usar o provedor de tipo WSDL para gerar tipos para o serviço da web TerraServer.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Para configurar o provedor de tipos e gerar tipos

1. Adicione a seguinte linha de código para abrir o namespace do provedor de tipo.
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. Adicione a seguinte linha de código para chamar o provedor de tipo com um serviço web. Neste exemplo, use o serviço da web TerraServer.
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  Um rabisco vermelho é exibido sob essa linha de código se o URI do serviço está incorreta ou se o próprio serviço está inativo ou não está executando. Se você apontar para o código, uma mensagem de erro descreve o problema. Você pode encontrar as mesmas informações no **lista de erros** janela ou a **a janela de saída** depois de criar.
<br />  Há duas maneiras de especificar definições de configuração para uma conexão de WSDL, usando o arquivo App. config para o projeto, ou usando os parâmetros de tipo estático na declaração do provedor de tipo. Você pode usar o svcutil.exe para gerar elementos do arquivo de configuração apropriado. Para obter mais informações sobre como usar o svcutil.exe para gerar informações de configuração para um serviço web, consulte [Ferramenta Utilitária de metadados ServiceModel &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx). Para obter uma descrição completa dos parâmetros de tipo estático para o provedor de tipo WSDL, consulte [provedor de tipos WsdlService](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>Chamar o serviço web e processar os resultados
Cada serviço web tem seu próprio conjunto de tipos que são usados como parâmetros para suas chamadas de método. Nesta etapa, esses parâmetros de preparação, chamar um método web e processar as informações que ele retorna.


#### <a name="to-call-the-web-service-and-process-the-results"></a>Para chamar o serviço web e processar os resultados

1. O serviço web pode atingir o tempo limite ou parar de funcionar, portanto você deve incluir a chamada de serviço da web em uma bloco de tratamento de exceções. Escreva o código a seguir para tentar obter dados do serviço da web.
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

Observe que você criar os tipos de dados que são necessários para o serviço web, tais como **local** e **local**, como o tipo de tipos aninhados sob o WsdlService **TerraService**.
<br />


## <a name="see-also"></a>Consulte também
[Provedor de tipos WsdlService](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[Provedores de Tipos](index.md)
