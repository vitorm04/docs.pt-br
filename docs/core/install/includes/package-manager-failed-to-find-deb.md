---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506943"
---

Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote {dotnet-Package}** ou **não foi possível instalar alguns pacotes** , execute os comandos a seguir.

Há dois espaços reservados no seguinte conjunto de comandos.

- `{dotnet-package}`\
Isso representa o pacote .NET que você está instalando, como `aspnetcore-runtime-3.1` . Isso é usado no comando a seguir `sudo apt-get install` .

- `{os-version}`\
Isso representa a versão do Linux em que você está. Isso é usado no `wget` comando a seguir.

Primeiro, tente limpar a lista de pacotes:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Em seguida, tente instalar o .NET novamente. Se isso não funcionar, você poderá executar uma instalação manual com os seguintes comandos:
