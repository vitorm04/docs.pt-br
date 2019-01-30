---
title: Assemblies de vários arquivos
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bad63bbc8e221f306e5807f51fbbb8eb4761d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599173"
---
# <a name="multifile-assemblies"></a>Assemblies de vários arquivos

Você pode criar assemblies de vários arquivos usando os compiladores de linha de comando ou o Visual Studio com o Visual C++. Um arquivo no assembly deve conter o manifesto do assembly. Um assembly que inicia um aplicativo também deve conter um ponto de entrada, como um método Main ou WinMain.

Por exemplo, suponha que você tenha um aplicativo que contém dois módulos de código, Client.cs e Stringer.cs. Stringer.cs cria o namespace `myStringer` que é referenciado pelo código em Client.cs. Client.cs contém o método `Main`, que é o ponto de entrada do aplicativo. Neste exemplo, você compila os dois módulos de código e cria um terceiro arquivo que contém o manifesto do assembly, que inicia o aplicativo. O manifesto do assembly faz referência aos módulos `Client` e `Stringer`.

> [!NOTE]
> Os assemblies de vários arquivos podem ter apenas um ponto de entrada, mesmo que o assembly tenha vários módulos de código.

Existem vários motivos que levam você a querer criar um assembly de vários arquivos:

-   Para combinar módulos escritos em linguagens diferentes. Essa é a razão mais comum para a criação de um assembly de vários arquivos.

-   Para otimizar o download de um aplicativo colocando tipos raramente usados em um módulo que é baixado apenas quando necessário.

    > [!NOTE]
    > Se você estiver criando aplicativos que serão baixados usando a marca `<object>` com o Microsoft Internet Explorer, é importante criar assemblies de vários arquivos. Nesse cenário, você cria um arquivo separado do seus módulos de código que contenha somente o manifesto do assembly. O Internet Explorer baixa o manifesto do assembly primeiro e, em seguida, cria threads de trabalho para baixar quaisquer módulos adicionais ou assemblies necessários. Enquanto o arquivo que contém o manifesto do assembly estiver sendo baixado, o Internet Explorer não responderá à entrada do usuário. Quanto menor o arquivo que contém o manifesto do assembly, menos tempo o Internet Explorer ficará sem responder.

-   Para combinar módulos de código escritos por vários desenvolvedores. Embora cada desenvolvedor possa compilar cada módulo de código em um assembly, isso pode forçar alguns tipos a serem expostos publicamente, que não o seriam se todos os módulos fossem colocados em um assembly de vários arquivos.

Depois de criar o assembly, você pode assinar o arquivo que contém o manifesto do assembly (e, portanto, o assembly) ou pode dar um nome forte ao arquivo (e ao assembly) e colocá-lo no cache de assembly global.

## <a name="see-also"></a>Consulte também

- [Como: Criar um assembly de vários arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)