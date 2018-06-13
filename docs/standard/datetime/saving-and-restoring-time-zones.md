---
title: Salvando e restaurando fusos horários
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7c9aefa08d837ce93e718ff32a463d95dabcdc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576250"
---
# <a name="saving-and-restoring-time-zones"></a>Salvando e restaurando fusos horários

O <xref:System.TimeZoneInfo> classe depende do registro para recuperar dados de fuso horário predefinidos. No entanto, o registro é uma estrutura dinâmica. Além disso, as informações de fuso horário que o registro contém são usadas pelo sistema operacional principalmente para tratar ajustes de tempo e conversões para o ano atual. Isso tem duas implicações principais para aplicativos que dependem de dados de fuso horário preciso:

* Um fuso horário que é exigido por um aplicativo não pode ser definido no registro, ou talvez tenham sido renomeado ou removido do registro.

* Um fuso horário definido no registro podem não ter informações sobre as regras de ajuste específicas que são necessárias para conversões de fuso horário históricos.

O <xref:System.TimeZoneInfo> classe aborda essas limitações através de seu suporte para serialização (Salvar) e desserialização (Restaurar) dos dados de fuso horário.

## <a name="time-zone-serialization-and-deserialization"></a>Fuso horário serialização e desserialização

Salvando e restaurando um fuso horário ao serializar e desserializar dados de fuso horário envolvem apenas duas chamadas de método:

* Você pode serializar um <xref:System.TimeZoneInfo> objeto chamando esse objeto <xref:System.TimeZoneInfo.ToSerializedString%2A> método. O método não usa nenhum parâmetro e retorna uma cadeia de caracteres que contém informações de fuso horário.

* Você pode desserializar um <xref:System.TimeZoneInfo> objeto a partir de uma cadeia de caracteres serializada, passando essa cadeia de caracteres para o `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> método.

## <a name="serialization-and-deserialization-scenarios"></a>Cenários de serialização e desserialização

A capacidade de salvar (ou serializar) um <xref:System.TimeZoneInfo> objeto para uma cadeia de caracteres e para restaurar (ou desserializar) para uso posterior aumenta tanto o utilidade e a flexibilidade do <xref:System.TimeZoneInfo> classe. Esta seção examina algumas das situações em que a serialização e desserialização são mais úteis.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serialização e desserialização de dados de fuso horário em um aplicativo

Um fuso horário serializado pode ser restaurado de uma cadeia de caracteres quando ela for necessária. Um aplicativo pode fazer isso, se o fuso horário recuperado do registro não é possível converter corretamente uma data e hora em um determinado intervalo de datas. Por exemplo, dados de fuso horário no registro do Windows XP oferece suporte a uma regra de ajuste simples, enquanto os fusos horários definidos no registro do Windows Vista normalmente fornecem informações sobre duas regras de ajuste. Isso significa que conversões históricos de tempo podem não ser precisas. Serialização e desserialização de dados de fuso horário podem lidar com essa limitação.

No exemplo a seguir, um personalizado <xref:System.TimeZoneInfo> classe com nenhuma regra de ajuste é definida para representar dos EUA Fuso horário padrão Oriental do 1883 para 1917, antes da introdução do horário de verão nos Estados Unidos. O fuso horário personalizado é serializado em uma variável com escopo global. O método de conversão de fuso horário, `ConvertUtcTime`, é passada tempos de tempo Universal Coordenado (UTC) para converter. Se a data e hora ocorrem em 1917 ou antes, o fuso horário padrão do Leste personalizado é restaurado a partir de uma cadeia de caracteres serializada e substitui o fuso horário recuperado do registro.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Tratamento de exceções de fuso horário

Como o registro é uma estrutura dinâmica, seu conteúdo está sujeito a modificação acidental ou intencional. Isso significa que um fuso horário que deve ser definida no registro e que é necessário para um aplicativo ser executado com êxito pode estar ausente. Sem suporte para o fuso horário a serialização e desserialização, você tem outra escolha ao tratar resultante <xref:System.TimeZoneNotFoundException> encerrando o aplicativo. No entanto, usando o fuso horário a serialização e desserialização, você pode manipular inesperado <xref:System.TimeZoneNotFoundException> restaurando a zona de tempo necessária de uma cadeia de caracteres serializada e o aplicativo continuará a ser executado.

O exemplo a seguir cria e serializa um fuso horário padrão Central personalizado. Em seguida, tenta recuperar o fuso horário padrão Central a partir do registro. Se a operação de recuperação gera uma <xref:System.TimeZoneNotFoundException> ou um <xref:System.InvalidTimeZoneException>, o manipulador de exceção desserializa o fuso horário.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Armazenar uma cadeia de caracteres serializada e restaurá-lo quando necessário

Os exemplos anteriores tem informações de fuso horário para uma variável de cadeia de caracteres armazenadas e restaurá-la quando necessário. No entanto, a cadeia de caracteres que contém o tempo serializado informações de zona podem ser próprio armazenadas em algum meio de armazenamento, como um arquivo externo, um arquivo de recurso incorporado do aplicativo ou o registro. (Observe que informações sobre fusos horários personalizados devem ser armazenadas além de chaves de fuso horário do sistema no registro.)

Armazenar uma cadeia de caracteres serializada de zona de tempo dessa forma também separa a rotina de criação de fuso horário do próprio aplicativo. Por exemplo, uma rotina de criação de fuso horário pode executar e criar um arquivo de dados que contém informações históricas de zona de tempo que um aplicativo pode usar. O arquivo de dados então pode ser instalado com o aplicativo e pode ser aberto e um ou mais dos seus fusos horários podem ser desserializados quando o aplicativo precisa deles.

Para obter um exemplo que usa um recurso incorporado para armazenar dados serializados de zona de tempo, consulte [como: salvar fusos horários em um recurso incorporado](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) e [como: restaurar fusos horários de um recurso incorporado](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
