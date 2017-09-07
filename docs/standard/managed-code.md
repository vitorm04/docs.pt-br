---
title: "O que é código gerenciado?"
description: "Saiba como o código gerenciado é o código cuja execução é gerenciada por um tempo de execução, o CLR (Common Language Runtime)."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: 263662c1c7f22c84e0de14c6480fa9807b46b2f2
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---

# <a name="what-is-managed-code"></a>O que é “código gerenciado”?

Ao trabalhar com o .NET Framework, geralmente você encontrará o termo "código gerenciado". Este documento explicará o que esse termo significa e obterá informações adicionais sobre ele.

Em resumo, código gerenciado é exatamente isso: código cuja execução é gerenciada por um tempo de execução. Nesse caso, o tempo de execução em questão é chamado de **Common Language Runtime** ou CLR, independentemente da implementação ([Mono](http://www.mono-project.com/) ou do .NET Framework ou .NET Core). CLR é responsável por pegar o código gerenciado, compilá-lo em código de computador e, em seguida, executá-lo. Além disso, o tempo de execução fornece vários serviços importantes, como gerenciamento automático de memória, limites de segurança, segurança de digitação etc.

Compare isso à maneira pela qual você executaria um programa C/C++, também chamado de "código não gerenciado". No mundo não gerenciado, o programador é responsável por quase tudo. O programa real é, essencialmente, um binário que o sistema operacional (SO) carrega na memória e inicia. Tudo, desde o gerenciamento da memória até as considerações de segurança, é responsabilidade do programador.

O código gerenciado é escrito em uma das linguagens de alto nível que podem ser executadas sobre o .NET, como C#, Visual Basic, F# e outras. Quando você compila o código gravado nessas linguagens com seu respectivo compilador, não obtém o código do computador. Você obtém o código de **Linguagem intermediária** que o tempo de execução compila e executa. C++ é a única exceção a essa regra, já que também pode produzir binários nativos e não gerenciados que são executados no Windows.

## <a name="intermediate-language--execution"></a>Linguagem intermediária e execução

O que é "Linguagem Intermediária" (ou IL)? É um produto de compilação de código gravado em linguagens .NET de alto nível. Quando você compila o código gravado em uma dessas linguagens, obtém um binário composto de IL. É importante observar que a IL é independente de qualquer linguagem específica executada em tempo de execução; há até mesmo uma especificação separada para que você pode ler se desejar.

Depois de gerar a IL do código de alto nível, execute-o. Aqui, a CLR assume e inicia o processo de compilação **Just-In-Time** ou **colocando em compilação JIT** seu código da IL no código do computador, que pode ser executado em uma CPU. Dessa forma, a CLR sabe exatamente o que o código está fazendo e pode, efetivamente, _gerenciá_-lo.

A Linguagem intermediária também é chamada CIL (Common Intermediate Language) ou MSIL (Microsoft Intermediate Language).

## <a name="unmanaged-code-interoperability"></a>Interoperabilidade de código não gerenciado

Naturalmente, a CLR permite passar os limites entre o mundo gerenciado e o não gerenciado e há muitos códigos que fazem isso, mesmo nas [Bibliotecas de classes base](framework-libraries.md). Isso é chamado de **interoperabilidade** ou apenas **interop**. Essas condições permitiriam, por exemplo, resumir uma biblioteca não gerenciada e chamá-la. No entanto, é importante observar que quando você faz isso, quando o código passa os limites do tempo de execução, o gerenciamento real da execução está novamente no código não gerenciado e, portanto, se enquadra nas mesmas restrições.

Semelhante a isso, C# é uma linguagem que permite que você use construções não gerenciadas como ponteiros diretamente no código, utilizando o que é conhecido como **contexto inseguro** que designa um trecho de código para o qual a execução não é gerenciada pela CLR.

## <a name="more-resources"></a>Mais recursos

*   [Visão geral conceitual do .NET Framework](https://msdn.microsoft.com/library/zw4w595w.aspx)
*   [Código não seguro e ponteiros](https://msdn.microsoft.com/library/t2yzs44b.aspx)
*   [Interoperabilidade (Guia de Programação em C#)](https://msdn.microsoft.com/library/ms173184.aspx)

