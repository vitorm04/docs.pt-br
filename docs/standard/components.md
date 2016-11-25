---
title: Componentes de arquitetura do .NET
description: "Descreve os principais componentes de arquitetura do .NET, como a .NET Standard Library, tempos de execução do .NET e ferramentas."
keywords: .NET, .NET Standard Library, .NET Standard, .NET Core, .NET Framework, Xamarin, MSBuild, C#, F#, VB e compiladores
author: cartermp
manager: wpickett
ms.author: cartermp
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 254e89abefd28419bd2f36a047e4df939f7ff8da
ms.openlocfilehash: d0cd8f44876038167db23e7fd1e5a893460f3d73

---

# <a name="net-architectural-components"></a>Componentes de arquitetura do .NET

O .NET é composto por diversos componentes-chave.  Um deles é a biblioteca padrão, denominada .NET Standard Library, que é um grande conjunto de APIs executados em todos os lugares.  Essa biblioteca padrão é implementada por três tempos de execução do .NET – .NET Framework, .NET Core e Mono para Xamarin.  As linguagens .NET também são executadas em qualquer tempo de execução do .NET.  Além disso, existem ferramentas em todas as plataformas que permitem criar projetos.  Essas ferramentas são as mesmas, independentemente do tempo de execução escolhido.

Veja uma visão geral gráfica de cada um dos componentes do .NET mencionados anteriormente e como eles se ajustam.

![Todos os componentes de arquitetura do .NET juntos](media/components.png)

O que vem a seguir é uma breve explicação de cada um dos principais componentes mostrados acima.  

## <a name="net-standard-library"></a>.NET Standard Library

A .NET Standard Library é um conjunto de APIs implementados por um tempo de execução do .NET.

De maneira mais formal, é uma especificação das APIs do .NET que compõem um conjunto uniforme de contratos nos quais você compila seu código.  Esses contratos têm implementações subjacentes para cada tempo de execução do .NET.  Isso possibilita portabilidade em diferentes tempos de execução do .NET, para que seu código possa ser "executado efetivamente em qualquer lugar".

A .NET Standard Library também é um destino de build, em que é conhecida como .NET Standard.  Atualmente, é possível direcionar o .NET Standard 1.0-1.6.  Caso o seu código tenha como alvo uma versão do .NET Standard, ele será executado em todos os tempos de execução que implementam essa versão.

Para saber mais sobre a biblioteca do .NET Standard e o direcionamento para o .NET Standard, consulte [.NET Standard Library](library.md).

## <a name="net-runtimes"></a>Tempos de execução do .NET

Há três tempos de execução primários do .NET que a Microsoft mantém e desenvolve ativamente: .NET Core, .NET Framework e Mono para Xamarin.

### <a name="net-core"></a>.NET Core

O .NET Core é um tempo de execução otimizado de plataforma cruzada para cargas de trabalho do servidor.  Ele implementa a .NET Standard Library, o que significa que códigos direcionados para o .NET Standard podem ser executados no .NET Core.  É o tempo de execução usado pelo ASP.NET Core e pela Plataforma Universal do Windows (UWP).  É moderno, eficiente e projetado para lidar com cargas de trabalho de servidor e nuvem em escala.

Para saber mais sobre o .NET Core, consulte o [Guia do .NET Core](../core/index.md).

### <a name="net-framework"></a>.NET Framework

O .NET Framework é o histórico tempo de execução do .NET, que existe desde 2002.  É o mesmo .NET Framework que os desenvolvedores do .NET sempre usaram.  Ele implementa a .NET Standard Library, o que significa que códigos direcionados para o .NET Standard podem ser executados no .NET Framework.  Ele contém APIs adicionais específicas do Windows, como APIs para desenvolvimento de área de trabalho do Windows com o Windows Forms e o WPF.  O .NET Framework é otimizado para a compilação de aplicativos da área de trabalho do Windows.

Para saber mais sobre o .NET Framework, consulte o [Guia do .NET Framework](../framework/index.md).

### <a name="mono-for-xamarin"></a>Mono para Xamarin

O Mono é o tempo de execução utilizado por aplicativos do Xamarin.  Ele implementa a .NET Standard Library, o que significa que códigos direcionados para o .NET Standard podem ser executados nos aplicativos do Xamarin.  Ele contém APIs adicionais para iOS, Android, Xamarin.Forms e Xamarin.Mac.  É otimizado para compilar aplicativos móveis no iOS e Android.

Para saber mais sobre o Mono, consulte a [Documentação do Mono](http://www.mono-project.com/docs/).

## <a name="net-tooling-and-common-infrastructure"></a>Ferramentas do .NET e infraestrutura comum

As ferramentas para .NET também são comuns em cada implementação do .NET.  Elas incluem (mas não se limitam a):

* As linguagens do .NET e seus compiladores
* Componentes de tempo de execução, como o JIT e o Coletor de Lixo
* Sistema de projeto do .NET (também conhecido como "csproj", "vbproj" ou "fsproj")
* MSBuild, o mecanismo de compilação usado para compilar projetos
* NuGet, o gerenciador de pacotes da Microsoft para o .NET
* A CLI do .NET, uma interface de linha de comando de plataforma cruzada para a compilação de projetos do .NET
* Ferramentas de orquestração compiladas em software livre, como CAKE e FAKE

A principal vantagem é que há uma grande quantidade de ferramentas e infraestrutura comuns para cada “versão” do .NET que você escolha para compilar seus aplicativos.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, visite:

* [.NET Standard Library](library.md)
* [Guia do .NET Core](../core/index.md)
* [Guia do .NET Framework](../framework/index.md)
* [Guia do C#](../csharp/index.md)
* [Guia do F#](../csharp/index.md)
* [Guia do VB.NET](../csharp/index.md)


<!--HONumber=Nov16_HO3-->


