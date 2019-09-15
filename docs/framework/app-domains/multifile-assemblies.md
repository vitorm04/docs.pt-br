---
title: Assemblies de multiarquivo
ms.date: 08/20/2019
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
ms.openlocfilehash: b4c288a54194e89eb90b6ac512cf45184376e952
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971873"
---
# <a name="multifile-assemblies"></a>Assemblies de multiarquivo

Você pode criar assemblies de multiarquivos destinados ao .NET Framework usando compiladores de linha de comando ou Visual Studio C++com Visual. Um arquivo no assembly deve conter o manifesto do assembly. Um assembly que inicia um aplicativo também deve conter um ponto de entrada, como um `Main` método `WinMain` ou.

Por exemplo, suponha que você tenha um aplicativo que contenha dois módulos de código, *Client.cs* e *Stringer.cs*. *Stringer.cs* cria o `myStringer` namespace que é referenciado pelo código em *Client.cs*. *Client.cs* contém o `Main` método, que é o ponto de entrada do aplicativo. Neste exemplo, você compila os dois módulos de código e cria um terceiro arquivo que contém o manifesto do assembly, que inicia o aplicativo. O manifesto do assembly faz referência aos módulos *cliente* e *Stringer* .

> [!NOTE]
> Os assemblies de vários arquivos podem ter apenas um ponto de entrada, mesmo que o assembly tenha vários módulos de código.

Existem vários motivos que levam você a querer criar um assembly de vários arquivos:

- Para combinar módulos escritos em linguagens diferentes. Essa é a razão mais comum para a criação de um assembly de vários arquivos.

- Para otimizar o download de um aplicativo colocando tipos raramente usados em um módulo que é baixado apenas quando necessário.

    > [!NOTE]
    > Se você estiver criando aplicativos que serão baixados usando a marca `<object>` com o Microsoft Internet Explorer, é importante criar assemblies de vários arquivos. Nesse cenário, você cria um arquivo separado do seus módulos de código que contenha somente o manifesto do assembly. O Internet Explorer baixa o manifesto do assembly primeiro e, em seguida, cria threads de trabalho para baixar quaisquer módulos adicionais ou assemblies necessários. Enquanto o arquivo que contém o manifesto do assembly estiver sendo baixado, o Internet Explorer não responderá à entrada do usuário. Quanto menor o arquivo que contém o manifesto do assembly, menos tempo o Internet Explorer ficará sem responder.

- Para combinar módulos de código escritos por vários desenvolvedores. Embora cada desenvolvedor possa compilar cada módulo de código em um assembly, isso pode forçar alguns tipos a serem expostos publicamente, que não o seriam se todos os módulos fossem colocados em um assembly de vários arquivos.

Depois de criar o assembly, você pode assinar o arquivo que contém o manifesto do assembly e, portanto, o assembly, ou pode dar ao arquivo e ao assembly um nome forte e colocá-lo no cache de assembly global.

## <a name="see-also"></a>Consulte também

- [Como: Compilar um assembly de multiarquivos](build-multifile-assembly.md)
- [Programa com assemblies](../../standard/assembly/program.md)
