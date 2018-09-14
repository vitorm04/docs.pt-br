---
title: 'Como: enumerar os fusos horários presentes em um computador'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c012b10f43a45699605e2d87a5b4a814c7dae28
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521590"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Como: enumerar os fusos horários presentes em um computador

Trabalhar com êxito com um fuso horário designado requer que informações sobre o fuso horário em questão estejam disponíveis no sistema. Os sistemas operacionais Windows XP e Windows Vista armazenar essas informações no registro. Embora o número total de fusos horários existentes seja grande, o Registro contém informações apenas sobre um subconjunto deles. Além disso, o Registro em si é uma estrutura dinâmica cujo conteúdo está sujeito a alterações deliberadas ou acidentais. Como resultado, um aplicativo nem sempre pode presumir que um determinado fuso horário esteja definido e disponível no sistema. A primeira etapa para muitos aplicativos que usam informações de fuso horário é determinar se os fusos horários necessários estão disponíveis no sistema local ou dar ao usuário uma lista dos fusos horários entre os quais escolher. Isso requer que o aplicativo enumere os fusos horários definidos no sistema local.

> [!NOTE]
> Se um aplicativo se baseia na presença de um determinado fuso horário que não podem ser definida em um sistema local, o aplicativo pode garantir sua presença ao serializar e desserializar as informações sobre o fuso horário. O fuso horário, em seguida, podem ser adicionado a um controle de lista para que o usuário do aplicativo pode selecioná-lo. Para obter detalhes, consulte [como: salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) e [como: restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Para enumerar os fusos horários presentes no sistema local

1. Chame o método <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. O método retorna um genérico <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> coleção de <xref:System.TimeZoneInfo> objetos. As entradas na coleção são classificadas por seus <xref:System.TimeZoneInfo.DisplayName%2A> propriedade. Por exemplo:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Enumerar o indivíduo <xref:System.TimeZoneInfo> objetos na coleção usando um `foreach` loop (em c#) ou um `For Each`...`Next` executar um loop (no Visual Basic) e executar qualquer processamento necessário em cada objeto. Por exemplo, o código a seguir enumera os <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> coleção de <xref:System.TimeZoneInfo> objetos retornados na etapa 1 e lista o nome de exibição de cada fuso horário no console.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Para apresentar ao usuário uma lista dos fusos horários presentes no sistema local

1. Chame o método <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. O método retorna um genérico <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> coleção de <xref:System.TimeZoneInfo> objetos.

2. Atribua a coleção retornada na etapa 1 para o `DataSource` propriedade de um Windows forms ou ASP.NET controle de lista.

3. Recuperar o <xref:System.TimeZoneInfo> objeto que o usuário selecionou.

O exemplo fornece uma ilustração de um aplicativo do Windows.

## <a name="example"></a>Exemplo

O exemplo inicia um aplicativo do Windows que exibe os fusos horários definidos em um sistema em uma caixa de listagem. O exemplo, em seguida, exibe uma caixa de diálogo que contém o valor da <xref:System.TimeZoneInfo.DisplayName%2A> propriedade do objeto de fuso horário selecionado pelo usuário.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Mais controles de lista (como o <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> ou <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> controle) permitem que você atribua uma coleção de variáveis de objeto para seus `DataSource` propriedade, desde que essa coleção implementa a <xref:System.Collections.IEnumerable> interface. (O genérico <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> classe faz isso.) Para exibir um objeto individual na coleção, o controle chama esse objeto `ToString` método para extrair a cadeia de caracteres que é usada para representar o objeto. No caso de <xref:System.TimeZoneInfo> objetos, o `ToString` método retorna o <xref:System.TimeZoneInfo> nome de exibição do objeto (o valor de seu <xref:System.TimeZoneInfo.DisplayName%2A> propriedade).

> [!NOTE]
> Porque um objeto de chamada de controles de lista `ToString` método, você pode atribuir uma coleção de <xref:System.TimeZoneInfo> objetos para o controle tem o controle exibir um nome significativo para cada objeto e recuperar o <xref:System.TimeZoneInfo> objeto que o usuário selecionou. Isso elimina a necessidade de extrair uma cadeia de caracteres para cada objeto na coleção, atribuir a cadeia de caracteres em uma coleção que por sua vez é atribuída ao controle de `DataSource` propriedade, recuperar a cadeia de caracteres que o usuário tiver selecionado e, em seguida, usar essa cadeia de caracteres para extrair o objeto que ele descreve. 

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência à dll seja adicionada ao projeto.

* Se os seguintes namespaces sejam importados:

  <xref:System> (no código do c#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Consulte também

* [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
* [Como salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
* [Como restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
