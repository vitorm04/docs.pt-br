---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: bfa7bcefff45bc325d7bba3aa2b9b3a8f0d439fa
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071930"
---
Crie um arquivo de texto chamado `azureauth.json`. Cole o saída do JSON exibida quando criou a entidade de serviço.

Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo. Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
