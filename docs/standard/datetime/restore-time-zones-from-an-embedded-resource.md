---
title: 'Como: restaurar fusos horários de um recurso inserido'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98813bf6685be78d33ebd5cc5e8c07a61a811c25
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106757"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Como: restaurar fusos horários de um recurso inserido

Este tópico descreve como restaurar os fusos horários que foram salvos em um arquivo de recurso. Para obter informações e instruções sobre como salvar fusos [horários, consulte Como: Salve fusos horários em um recurso](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)inserido.

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Para desserializar um objeto TimeZoneInfo de um recurso inserido

1. Se o fuso horário a ser recuperado não for um fuso horário personalizado, tente instanciá-lo usando o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método.

2. Crie uma <xref:System.Resources.ResourceManager> instância de um objeto passando o nome totalmente qualificado do arquivo de recurso inserido e uma referência para o assembly que contém o arquivo de recurso.

   Se você não puder determinar o nome totalmente qualificado do arquivo de recurso inserido, use o [ILDASM. exe (desmontador de Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar o manifesto do assembly. Uma `.mresource` entrada identifica o recurso. No exemplo, o nome totalmente qualificado do recurso é `SerializeTimeZoneData.SerializedTimeZones`.

   Se o arquivo de recurso for inserido no mesmo assembly que contém o código de instanciação de fuso horário, você poderá recuperar uma referência a ele chamando `static` o`Shared` método (no <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> Visual Basic).

3. Se a chamada para o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método falhar ou se um fuso horário personalizado for ser instanciado, recupere uma cadeia de caracteres que contenha o fuso horário serializado chamando o <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> método.

4. Desserializar os dados de fuso horário chamando o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.

## <a name="example"></a>Exemplo

O exemplo a seguir desserializa um <xref:System.TimeZoneInfo> objeto armazenado em um arquivo de recurso XML do .net inserido.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Esse código ilustra a manipulação de exceção para garantir <xref:System.TimeZoneInfo> que um objeto exigido pelo aplicativo esteja presente. Primeiro, ele tenta criar uma <xref:System.TimeZoneInfo> instância de um objeto recuperando-o do registro <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> usando o método. Se o fuso horário não puder ser instanciado, o código o recuperará do arquivo de recurso inserido.

Como os dados de fusos horários personalizados (fusos horários instanciados <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> usando o método) não são armazenados no registro, o código não chama o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> para instanciar o fuso horário para Palmer, Antártica. Em vez disso, ele procura imediatamente o arquivo de recurso inserido para recuperar uma cadeia de caracteres que contém os dados do fuso horário <xref:System.TimeZoneInfo.FromSerializedString%2A> antes de chamar o método.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que uma referência a System. Windows. Forms. dll e System. Core. dll seja adicionada ao projeto.

- Que os seguintes namespaces sejam importados:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
- [Como: Salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
