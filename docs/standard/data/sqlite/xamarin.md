---
title: Limitações do Xamarin
ms.date: 12/13/2019
description: Descreve algumas das limitações que você encontrará ao usar o Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447163"
---
# <a name="xamarin-limitations"></a>Limitações do Xamarin

O Microsoft. Data. sqlite tem como destino .NET Standard 2,0 e tem suporte no Xamarin. A tabela a seguir mostra quais plataformas o pacote SQLitePCLRaw padrão fornece binários do SQLite nativos para o. Consulte [versões personalizadas do SQLite](custom-versions.md) para obter detalhes sobre como usar um pacote diferente ou fornecer seus próprios binários do SQLite nativos.

| Platform | Binários do SQLite |
| --- | --- |
| **Xamarin.Android** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | ✔ |
| **Xamarin.iOS** | ✔ |
| **Xamarin.Mac** | ✔ |
| **Xamarin. TVOS** | ✔ |
| **UWP** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |

## <a name="ios"></a>iOS

Microsoft. Data. sqlite tenta inicializar automaticamente os pacotes de SQLitePCLRaw. Infelizmente, devido a limitações na compilação da AOT (antecipadamente de tempo) para Xamarin. iOS, a tentativa falha e você obtém o erro a seguir.

> Você precisa chamar `SQLitePCL.raw.SetProvider()`. Se você estiver usando um pacote de pacotes, isso é feito chamando `SQLitePCL.Batteries.Init()`.

Para inicializar o pacote, adicione a seguinte linha de código ao seu aplicativo antes de usar o Microsoft. Data. sqlite.

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a>Veja também

* [Limitações assíncronas](async.md)
* [Versões personalizadas do SQLite](custom-versions.md)
