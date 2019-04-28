---
title: 'Como: salvar fusos horários em um recurso inserido'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912698"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Como: salvar fusos horários em um recurso inserido

Um aplicativo com reconhecimento de fuso horário geralmente exige a presença de um determinado fuso horário. No entanto, como a disponibilidade do indivíduo <xref:System.TimeZoneInfo> objetos depende de informações armazenadas no registro do sistema local, fusos horários disponíveis até mesmo normalmente pode estar ausentes. Além disso, informações sobre fusos horários personalizados é instanciado usando o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método não são armazenadas com outras informações de fuso horário no registro. Para garantir que essas zonas de tempo estejam disponíveis quando eles forem necessários, salvá-los ao serializá-los e depois restaurá-los por desserializá-las.

Normalmente, serializar uma <xref:System.TimeZoneInfo> objeto ocorre além do aplicativo com reconhecimento de fuso horário. Dependendo do armazenamento de dados usado para manter serializado <xref:System.TimeZoneInfo> objetos, dados de fuso horário podem ser serializados como parte de uma rotina de instalação (por exemplo, quando os dados são armazenados em uma chave do registro de aplicativo), ou como parte de uma rotina de utilitário que é executado antes do aplicativo final é compilado (por exemplo, quando os dados serializados são armazenados em um arquivo de recurso (. resx) de XML do .NET).

Além de um arquivo de recurso que é compilado com o aplicativo, vários outros armazenamentos de dados podem ser usados para obter informações de fuso horário. Eles incluem o seguinte:

* O registro. Observe que um aplicativo deve usar as subchaves da sua própria chave de aplicativo para armazenar dados de fuso horário personalizado em vez de utilizar as subchaves de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.

* Arquivos de configuração.

* Outros arquivos do sistema.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Para salvar uma zona de tempo serializando-a para um arquivo. resx

1. Recuperar uma zona de tempo existente ou crie um novo fuso horário.

   Para recuperar uma zona de tempo existente, consulte [como: Acessar os objetos de fuso horário UTC e local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md) e [como: Criar uma instância de um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Para criar um novo fuso horário, chame uma das sobrecargas do <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método. Para obter mais informações, confira [Como: Criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) e [como: Criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Chamar o <xref:System.TimeZoneInfo.ToSerializedString%2A> método para criar uma cadeia de caracteres que contém os dados do fuso horário.

3. Criar uma instância de um <xref:System.IO.StreamWriter> objeto, fornecendo o nome e, opcionalmente, o caminho do arquivo. resx para o <xref:System.IO.StreamWriter> construtor de classe.

4. Criar uma instância de um <xref:System.Resources.ResXResourceWriter> objeto, passando a <xref:System.IO.StreamWriter> do objeto para o <xref:System.Resources.ResXResourceWriter> construtor de classe.

5. Passe o fuso horário serializada de cadeia de caracteres para o <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> método.

6. Chame o método <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>.

7. Chame o método <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType>.

8. Fechar o <xref:System.IO.StreamWriter> objeto chamando seu <xref:System.IO.StreamWriter.Close%2A> método.

9. Adicione o arquivo. resx gerado ao projeto do Visual Studio do aplicativo.

10. Usando o **propriedades** janela no Visual Studio, certifique-se de que o arquivo. resx **Build Action** estiver definida como **Embedded Resource**.

## <a name="example"></a>Exemplo

O exemplo a seguir serializa um <xref:System.TimeZoneInfo> objeto que representa o horário padrão Central e um <xref:System.TimeZoneInfo> objeto que representa a Estação Palmer, a hora da Antártida para um arquivo de recurso XML .NET chamado SerializedTimeZones. Horário padrão Central normalmente é definido no registro. Estação Palmer, Antártica é um fuso horário personalizado.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Este exemplo serializa <xref:System.TimeZoneInfo> objetos para que eles estejam disponíveis em um arquivo de recurso em tempo de compilação.

Porque o <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> método adiciona informações de cabeçalho completo para um arquivo de recurso XML .NET, ele não pode ser usado para adicionar recursos a um arquivo existente. O exemplo lida com isso verificando o arquivo SerializedTimeZones e, se ele existir, armazenando todos os seus recursos diferentes dois serializado fusos horários um genérico <xref:System.Collections.Generic.Dictionary%602> objeto. O arquivo existente é excluído e os recursos existentes são adicionados a um novo arquivo SerializedTimeZones. Os dados da zona de tempo serializado também são adicionados a esse arquivo.

A chave (ou **nome**) campos de recursos não devem conter espaços inseridos. O <xref:System.String.Replace%28System.String%2CSystem.String%29> método é chamado para remover todos os espaços inseridos em identificadores de fuso horário, antes que eles sejam atribuídos ao arquivo de recurso.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência à dll e dll seja adicionada ao projeto.

* Se os seguintes namespaces sejam importados:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
- [Como: Restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
