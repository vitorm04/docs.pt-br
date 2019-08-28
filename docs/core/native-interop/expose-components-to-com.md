---
title: Expor componentes do .NET Core ao COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 33574eeac5b1f7aa2067b1974f3f2e68fb22e8ff
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577168"
---
# <a name="exposing-net-core-components-to-com"></a>Expor componentes do .NET Core ao COM

No .NET Core, o processo de expor seus objetos .NET ao COM foi significativamente simplificado em comparação com o .NET Framework. O processo a seguir explicará como expor uma classe ao COM. Este tutorial mostra como:

- Expor uma classe ao COM do .NET Core.
- Gerar um servidor COM como parte de criar sua biblioteca do .NET Core.
- Gerar automaticamente um manifesto de servidor lado a lado para COM Sem Registro.

## <a name="prerequisites"></a>Pré-requisitos

- Instale o [SDK do .NET Core 3.0 Versão Prévia 7](https://www.microsoft.com/net/core) ou uma versão mais recente.

## <a name="create-the-library"></a>Criar a biblioteca

A primeira etapa é criar a biblioteca.

1. Crie uma pasta e execute `dotnet new classlib` nela.
2. Abra `Class1.cs`.
3. Adicione `using System.Runtime.InteropServices;` ao topo do arquivo.
4. Crie uma interface chamada `IServer`. Por exemplo: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]
5. Adicione o atributo `[Guid("<IID>")]` à interface, com o GUID da interface COM que você está implementando. Por exemplo, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Observe que esse GUID precisa ser exclusivo, pois é o único identificador dessa interface para COM. No Visual Studio, você pode gerar um GUID acessando Ferramentas > Criar GUID para abrir a ferramenta Criar GUID.
6. Adicione o atributo `[InterfaceType]` à interface e especifique quais interfaces COM base sua interface deve implementar.
7. Crie uma classe chamada `Server` que implementa `IServer`.
8. Adicione o atributo `[Guid("<CLSID>")]` à classe, com o GUID do identificador de classe da classe COM que você está implementando. Por exemplo, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Como ocorre com o GUID da interface, esse GUID deve ser exclusivo pois é o único identificador dessa interface para COM.
9. Adicione o atributo `[ComVisible(true)]` à interface e à classe.

> [!IMPORTANT]
> Diferentemente do .NET Framework, o .NET Core exige que você especifique o CLSID de qualquer classe que você deseja que seja ativável por meio do COM.

## <a name="generate-the-com-host"></a>Gerar o host COM

1. Abra o arquivo de projeto `.csproj` e adicione `<EnableComHosting>true</EnableComHosting>` dentro de uma marca `<PropertyGroup></PropertyGroup>`.
2. Compile o projeto.

A saída resultante terá um arquivo `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` e `ProjectName.comhost.dll`.

## <a name="register-the-com-host-for-com"></a>Registrar o host COM para COM

Abra um prompt de comandos com privilégios elevados e execute `regsvr32 ProjectName.comhost.dll`. Isso registrará todos os seus objetos .NET expostos com o COM.

## <a name="enabling-regfree-com"></a>Habilitar o COM RegFree

1. Abra o arquivo de projeto `.csproj` e adicione `<EnableRegFreeCom>true</EnableRegFreeCom>` dentro de uma marca `<PropertyGroup></PropertyGroup>`.
2. Compile o projeto.

A saída resultante agora também terá um arquivo `ProjectName.X.manifest`. Esse arquivo é o manifesto lado a lado para uso com o COM Sem Registro.

## <a name="sample"></a>Amostra

Há um [exemplo de servidor COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) totalmente funcional no repositório dotnet/de exemplos no GitHub.

## <a name="additional-notes"></a>Observações Adicionais

Ao contrário do .NET Framework, não há suporte no .NET Core para gerar um TLB (Biblioteca de Tipos) COM com base em um assembly .NET Core. Você terá que escrever manualmente um arquivo IDL ou um cabeçalho C++ para as declarações nativas de suas interfaces.

Além disso, não há suporte para o carregamento do .NET Framework e do .NET Core no mesmo processo; em decorrência disso, não há suporte para o carregamento um servidor COM do .NET Core para um processo de cliente COM do .NET Framework ou vice-versa.
