---
title: 'Como: criar fusos horários sem regras de ajuste'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026543"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Como: criar fusos horários sem regras de ajuste

As informações precisas de fuso horário que são exigidas por um aplicativo não podem estar presentes em um determinado sistema por diversos motivos:

* O fuso horário nunca foi definido no registro do sistema local.

* Dados sobre o fuso horário foi modificados ou removidos do registro.

* O fuso horário existe, mas não tem informações precisas sobre ajustes de fuso horário para um determinado período de histórico.

Nesses casos, você pode chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método para definir o fuso horário exigido pelo seu aplicativo. Você pode usar as sobrecargas desse método para criar um fuso horário com ou sem regras de ajuste. Se o fuso horário der suporte ao horário de verão, você pode definir ajustes com a regras de ajuste fixa ou flutuante. (Para obter definições desses termos, consulte a seção "Terminologia de fuso horário" em [visão geral do fuso horário](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Fusos horários personalizados criados ao chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método não são adicionados ao registro. Em vez disso, eles podem ser acessados apenas pela referência de objeto retornada pelo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> chamada de método.

Este tópico mostra como criar um fuso horário sem regras de ajuste. Para criar um fuso horário que dá suporte a regras de ajuste de horário de verão, consulte [como: Criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Para criar um fuso horário sem regras de ajuste

1. Defina nome de exibição do fuso horário.

   O nome de exibição segue um formato padrão no qual o deslocamento do fuso horário do tempo Universal Coordenado (UTC) é colocado entre parênteses e é seguido por uma cadeia de caracteres que identifica o fuso horário, uma ou mais das cidades no fuso horário ou em um ou mais do cou ntries ou regiões no fuso horário.

2. Defina o nome do horário de padrão do fuso horário. Normalmente, essa cadeia de caracteres também é usada como identificador do fuso horário.

3. Se você quiser usar um identificador diferente do nome do padrão do fuso horário, defina o identificador de fuso horário.

4. Criar uma instância de um <xref:System.TimeSpan> objeto que define o deslocamento do fuso horário do UTC. Fusos horários com horários posteriores ao UTC têm um deslocamento positivo. Fusos horários com horários anteriores ao UTC têm um deslocamento negativo.

5. Chamar o <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> método para instanciar o novo fuso horário.

## <a name="example"></a>Exemplo

O exemplo a seguir define um fuso horário personalizado para Mawson, Antártica, que não tem a nenhuma regra de ajuste.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

A cadeia de caracteres atribuída para o <xref:System.TimeZoneInfo.DisplayName%2A> propriedade segue um formato padrão no qual o deslocamento do fuso horário do UTC é seguido por uma descrição amigável do fuso horário.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência à dll seja adicionada ao projeto.

* Se os seguintes namespaces sejam importados:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
- [Como: Criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
