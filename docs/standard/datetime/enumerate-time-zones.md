---
title: "Como enumerar os fusos horários presentes em um computador"
description: "Como enumerar os fusos horários presentes em um computador"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 5f385636137777013b540e8c1233751624139859

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Como enumerar os fusos horários presentes em um computador

Trabalhar com êxito com um fuso horário designado requer que informações sobre o fuso horário em questão estejam disponíveis no sistema. Por exemplo, o sistema operacional Windows armazena essas informações no Registro. Embora o número total de fusos horários existentes seja grande, o Registro contém informações apenas sobre um subconjunto deles. Além disso, o Registro em si é uma estrutura dinâmica cujo conteúdo está sujeito a alterações deliberadas ou acidentais. Como resultado, um aplicativo nem sempre pode presumir que um determinado fuso horário esteja definido e disponível no sistema. A primeira etapa para muitos aplicativos que usam informações de fuso horário é determinar se os fusos horários necessários estão disponíveis no sistema local ou dar ao usuário uma lista dos fusos horários entre os quais escolher. Isso requer que o aplicativo enumere os fusos horários definidos no sistema local. 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Para enumerar os fusos horários presentes no sistema local

1. Chame o método [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones). O método retorna uma coleção [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) genérica de objetos [TimeZoneInfo](xref:System.TimeZoneInfo). As entradas na coleção são classificadas segundo a propriedade [DisplayName](xref:System.TimeZoneInfo.DisplayName). Por exemplo:

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. Enumere os objetos [TimeZoneInfo](xref:System.TimeZoneInfo) individuais na coleção usando um loop `foreach` (em C#) ou um loop `For Each…Next` (no Visual Basic) e execute o processamento que for necessário em cada objeto. Por exemplo, o código a seguir enumera a coleção [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) dos objetos [TimeZoneInfo](xref:System.TimeZoneInfo) retornados na etapa 1 e lista o nome de exibição de cada fuso horário no console.

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md)




<!--HONumber=Dec16_HO1-->


