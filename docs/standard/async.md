---
title: "Visão geral da assincronia"
description: "Visão geral da assincronia"
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: b967d8e55347f44a012e4ad8e916440ae228c8ec
ms.openlocfilehash: db4c9721381a9675b06f0fc6b5381d987816e9a4
ms.lasthandoff: 03/10/2017

---

# <a name="async-overview"></a>Visão geral da assincronia

Não muito tempo atrás, os aplicativos ficavam mais rápidos simplesmente comprando um computador ou servidor mais novo e então essa tendência parou. Na verdade, ela foi invertida. Surgiram telefones celulares com chips ARM de núcleo único de 1 GHz e as cargas de trabalho do servidor passaram para VMs. Os usuários ainda querem uma interface do usuário responsiva e os proprietários de negócios querem servidores que ajustem a escala com seus negócios. A transição para celular e nuvem e uma população conectada à Internet de >3B usuários resultaram em um novo conjunto de padrões de software. 

* Os aplicativos cliente devem estar sempre ativos, sempre conectados e constantemente responsivos à interação do usuário (por exemplo, toque) com classificações altas na loja de aplicativos!
* Os serviços devem lidar com picos de tráfego escalando e reduzindo horizontalmente sem problemas. 

A programação assíncrona é uma técnica chave que torna fácil de lidar com o bloqueio de E/S e operações simultâneas em vários núcleos. O .NET fornece a capacidade para os aplicativos e serviços serem responsivos e elásticos com modelos de programação assíncrona fáceis de usar e em nível de linguagem em C#, VB e F#.

## <a name="why-write-async-code"></a>Por que escrever código assíncrono?

Os aplicativos modernos fazem amplo uso de E/S de arquivos e rede. As APIs de E/S tradicionalmente bloqueiam por padrão, resultando em experiências de usuário e utilização de hardware ruins, a menos que você deseje aprender e usar padrões desafiadores. O modelo de programação assíncrona em nível de linguagem e as APIs assíncronas invertem esse modelo, tornando a execução assíncrona o padrão com poucos novos conceitos para aprender.

O código assíncrono tem as seguintes características:

* Lida com mais solicitações de servidor gerando threads para lidar com mais solicitações enquanto espera as solicitações de E/S retornarem.
* Permite que as interfaces do usuário sejam mais responsivas gerando threads para a interação da interface do usuário enquanto espera as solicitações de E/S e fazendo a transição do trabalho de longa execução para outros núcleos de CPU.
* Muitas das APIs do .NET mais novas são assíncronas.
* É muito fácil escrever código assíncrono no .NET!

## <a name="whats-next"></a>O que vem a seguir?

Para aprofundar em conceitos de assincronia e programação, consulte [Assincronia detalhada](async-in-depth.md).


