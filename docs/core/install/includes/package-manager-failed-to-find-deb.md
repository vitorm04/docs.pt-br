---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132932"
---

Se você receber uma mensagem de erro semelhante a **não é possível localizar o pacote {NetCore-Package}** ou **alguns pacotes não puderam ser instalados**, execute os comandos a seguir.

Há dois espaços reservados no seguinte conjunto de comandos.

- `{dotnet-package}`\
Isso representa o pacote .NET Core que você está instalando, como `aspnetcore-runtime-3.1` . Isso é usado no `sudo apt-get install` comando a seguir.

- `{os-version}`\
Isso representa a versão do Linux em que você está. Isso é usado no `wget` comando a seguir.

Primeiro, tente limpar a lista de pacotes:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

Em seguida, tente instalar o .NET Core novamente. Se isso não funcionar, você poderá executar uma instalação manual com os seguintes comandos:
