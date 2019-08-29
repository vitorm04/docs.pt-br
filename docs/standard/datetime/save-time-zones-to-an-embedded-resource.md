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
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107154"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Como: salvar fusos horários em um recurso inserido

Um aplicativo com reconhecimento de fuso horário geralmente requer a presença de um fuso horário específico. No entanto, como a disponibilidade <xref:System.TimeZoneInfo> de objetos individuais depende das informações armazenadas no registro do sistema local, até mesmo normalmente os fusos horários disponíveis podem estar ausentes. Além disso, as informações sobre fusos horários personalizados instanciados usando <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> o método não são armazenadas com outras informações de fuso horário no registro. Para garantir que esses fusos horários estejam disponíveis quando forem necessários, você pode salvá-los serializando-os e depois restaurá-los desserializando-os.

Normalmente, a serialização <xref:System.TimeZoneInfo> de um objeto ocorre além do aplicativo com reconhecimento de fuso horário. Dependendo do armazenamento de dados usado para manter objetos serializados <xref:System.TimeZoneInfo> , os dados de fuso horário podem ser serializados como parte de uma rotina de instalação ou instalação (por exemplo, quando os dados são armazenados em uma chave de aplicativo do registro) ou como parte de uma rotina de utilitário que é executada antes de o aplicativo final ser compilado (por exemplo, quando os dados serializados são armazenados em um arquivo de recurso XML do .NET (. resx)).

Além de um arquivo de recurso que é compilado com o aplicativo, vários outros armazenamentos de dados podem ser usados para informações de fuso horário. Eles incluem o seguinte:

- O registro. Observe que um aplicativo deve usar as subchaves de sua própria chave de aplicativo para armazenar dados de fuso horário personalizados em vez de usar as subchaves das zonas HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Nt\currentversion\time Zones.

- Arquivos de configuração.

- Outros arquivos do sistema.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Para salvar um fuso horário serializando-o para um arquivo. resx

1. Recupere um fuso horário existente ou crie um novo fuso horário.

   Para recuperar um fuso horário existente, consulte [como: Acesse os objetos](../../../docs/standard/datetime/access-utc-and-local.md) predefinidos UTC e fuso [horário local e como: Crie uma instância de](../../../docs/standard/datetime/instantiate-time-zone-info.md)um objeto TimeZoneInfo.

   Para criar um novo fuso horário, chame uma das sobrecargas do <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método. Para obter mais informações, confira [Como: Crie fusos horários sem regras](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) de [ajuste e como: Crie fusos horários com regras](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)de ajuste.

2. Chame o <xref:System.TimeZoneInfo.ToSerializedString%2A> método para criar uma cadeia de caracteres que contenha os dados do fuso horário.

3. Crie uma <xref:System.IO.StreamWriter> instância de um objeto fornecendo o nome e, opcionalmente, o caminho do arquivo. <xref:System.IO.StreamWriter> resx para o construtor de classe.

4. Crie uma <xref:System.Resources.ResXResourceWriter> instância de um objeto <xref:System.IO.StreamWriter> passando o objeto <xref:System.Resources.ResXResourceWriter> para o construtor de classe.

5. Passe a cadeia de caracteres serializada do fuso <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> horário para o método.

6. Chame o método <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>.

7. Chame o método <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType>.

8. Feche o <xref:System.IO.StreamWriter> objeto chamando seu <xref:System.IO.StreamWriter.Close%2A> método.

9. Adicione o arquivo. resx gerado ao projeto do Visual Studio do aplicativo.

10. Usando a janela **Propriedades** no Visual Studio, certifique-se de que a propriedade de **ação de compilação** do arquivo. resx esteja definida como **recurso incorporado**.

## <a name="example"></a>Exemplo

O exemplo a seguir serializa um <xref:System.TimeZoneInfo> objeto que representa o horário padrão central e <xref:System.TimeZoneInfo> um objeto que representa a estação Palmer, a hora da Antártica, para um arquivo de recurso XML do .NET chamado SerializedTimeZones. resx. O horário padrão central normalmente é definido no registro; Estação Palmer, Antártica é um fuso horário personalizado.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Este exemplo serializa <xref:System.TimeZoneInfo> os objetos para que estejam disponíveis em um arquivo de recurso no momento da compilação.

Como o <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> método adiciona informações completas de cabeçalho a um arquivo de recurso XML do .net, ele não pode ser usado para adicionar recursos a um arquivo existente. O exemplo trata disso verificando o arquivo SerializedTimeZones. resx e, se ele existir, armazenando todos os seus recursos além dos dois fusos horários serializados para um <xref:System.Collections.Generic.Dictionary%602> objeto genérico. O arquivo existente é excluído e os recursos existentes são adicionados a um novo arquivo SerializedTimeZones. resx. Os dados de fuso horário serializados também são adicionados a esse arquivo.

Os campos de chave (ou **nome**) dos recursos não devem conter espaços incorporados. O <xref:System.String.Replace%28System.String%2CSystem.String%29> método é chamado para remover todos os espaços inseridos nos identificadores de fuso horário antes que eles sejam atribuídos ao arquivo de recurso.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Que uma referência a System. Windows. Forms. dll e System. Core. dll seja adicionada ao projeto.

- Que os seguintes namespaces sejam importados:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
- [Como: Restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
