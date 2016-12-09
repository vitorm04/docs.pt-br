---
title: Coleta de Lixo
description: Coleta de Lixo
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.devlang: dotnet
ms.assetid: db39a0f5-e363-490f-a7e6-adb9a6ff2a8c
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: c040a992b91ae27398264709aaa31440cea677f5

---

# <a name="garbage-collection"></a>Coleta de lixo

Coleta de lixo é um dos recursos mais importantes da plataforma de código gerenciado do .NET. O coletor de lixo (GC) gerencia para você a alocação e liberação de memória. Você não precisa saber como alocar e liberar memória ou gerenciar o tempo de vida dos objetos que usam essa memória. Uma alocação é feita sempre que você _novo_ um objeto ou um tipo de valor é colocado em caixa. As alocações são geralmente muito rápidas. Quando não houver memória suficiente para alocar um objeto, o GC deverá coletar e eliminar de memória de lixo para tornar mais memória disponível para novas alocações. Esse processo é chamado de "coleta de lixo".

O coletor de lixo atua como um gerenciador automático de memória. Ele oferece os seguintes benefícios:

*   Permite que você desenvolva seu aplicativo sem a necessidade de liberar memória.
*   Aloca objetos no heap gerenciado com eficiência.
*   Recupera os objetos que não estão sendo usados, limpa a memória e mantém a memória disponível para alocações futuras. Os objetos gerenciados obtêm automaticamente conteúdo limpo com o qual começar, portanto, seus construtores não precisam inicializar cada campo de dados.
*   Fornece segurança de memória, assegurando que um objeto não possa usar o conteúdo de outro objeto.

O .NET GC é geracional e tem 3 gerações. Cada geração tem seu próprio heap que ela usa para o armazenamento de objetos alocados. Há um princípio básico de que a maioria dos objetos são de vida útil curta ou então longa. A geração 0 é aquela na qual os objetos são alocados primeiro. Objetos muitas vezes não duram após a primeira geração, pois eles não estão mais em uso (fora do escopo) quando a próxima coleta de lixo ocorre. A geração 0 é de coleta rápida, porque seu heap associado é pequeno. A geração 1 é, na verdade, um espaço que funciona como uma segunda chance. Objetos de vida útil curta, mas que sobrevivem à coleta da geração 0 (geralmente devido a uma coincidência dos tempos) vão para a geração 1\. Coletas de geração 1 também são rápidas, porque seu heap associado também é pequeno. Os dois primeiros heaps permanecem pequenos porque os objetos são coletados ou então são promovidos para o heap da próxima geração. A geração 2 é aquela em que todos os objetos de vida útil longa estão. O heap da geração 2 pode crescer até ficar muito grande, considerando que os objetos que ele contém podem sobreviver por muito tempo e não há nenhum heap de geração 3 para promover ainda mais os objetos.

O GC tem um heap adicional para objetos grandes, chamado de Heap de Objeto Grande (LOH). Ele é reservado para objetos com 85.000 bytes ou mais. Uma matriz de bytes (Byte[]) com 85 mil elementos seria um exemplo de objeto grande. Objetos grandes não são alocados para os heaps geracionais, mas sim alocados diretamente para o LOH.

Coletas de geração 2 e de LOH podem levar um tempo considerável para programas que foram executados por um longo tempo ou que operam com grandes quantidades de dados. Programas de servidor de grande conhecidos por terem heaps com dezenas de GBs. O GC emprega uma variedade de técnicas para reduzir a quantidade de tempo pelo qual bloqueia a execução do programa. A abordagem principal consiste em fazer tanto trabalho de coleta de lixo quanto possível em um thread em segundo plano, de modo que isso não interfira na execução do programa. O GC também expõe algumas maneiras para desenvolvedores influenciarem seu comportamento, o que pode ser muito útil para melhorar o desempenho.

## <a name="related-topics"></a>Tópicos relacionados

Título | Descrição
----- | ----------- 
[Gerenciamento automático de memória e coleta de lixo](gc.md) | Apresenta os conceitos básicos de gerenciamento de memória no .NET
[Noções básicas da coleta de lixo](fundamentals.md) | Descreve como funciona a coleta de lixo, como os objetos são alocados no heap gerenciado e outros conceitos principais.
[Coletas induzidas](induced.md) | Descreve como fazer uma coleta de lixo ocorrer.
[Modos de latência](latency.md) | Descreve os modos de determinam o grau de intrusão da coleta de lixo.
[Referências fracas](weak-references.md) | Descreve os recursos que permitem que um objeto seja, simultaneamente, coletado pelo coletor de lixo e acessado pelo aplicativo.
 
## <a name="reference"></a>Referência

[System.GC](xref:System.GC)

[System.GCCollectionMode](xref:System.GCCollectionMode)

[System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode)

[System.Runtime.GCSettings](xref:System.Runtime.GCSettings)

[GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode)

[Object.Finalize](xref:System.Object.Finalize)

[System.IDisposable](xref:System.IDisposable)

## <a name="see-also"></a>Consulte também

[Limpando recursos não gerenciados](unmanaged.md)




<!--HONumber=Nov16_HO4-->


