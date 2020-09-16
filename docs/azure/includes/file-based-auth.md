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
<span data-ttu-id="2571b-101">Crie um arquivo de texto chamado `azureauth.json`.</span><span class="sxs-lookup"><span data-stu-id="2571b-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="2571b-102">Cole o saída do JSON exibida quando criou a entidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="2571b-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="2571b-103">Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo.</span><span class="sxs-lookup"><span data-stu-id="2571b-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="2571b-104">Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2571b-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
