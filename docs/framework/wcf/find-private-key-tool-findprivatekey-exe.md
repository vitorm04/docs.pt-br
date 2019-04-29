---
title: Encontrar ferramenta de chave privada (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 8f156cbb2f4fad8d51e356bd4dee2d72d9397ffb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929578"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Encontrar ferramenta de chave privada (FindPrivateKey.exe)

Essa ferramenta de linha de comando pode ser usada para recuperar uma chave privada de um repositório de certificados. Por exemplo, *FindPrivateKey.exe* pode ser usado para localizar o local e o nome do arquivo de chave privada associado com um certificado x. 509 específico no repositório de certificados.

> [!IMPORTANT]
> A ferramenta FindPrivateKey é fornecida como um exemplo do WCF. Para obter mais informações sobre onde encontrar o exemplo e como criá-lo, consulte [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Sintaxe

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Comentários

As tabelas a seguir descrevem os argumentos e as opções que podem ser usadas com a ferramenta de localizar a chave privada (FindPrivateKey.exe).

|Argumento|Descrição|
|--------------|-----------------|
|`storeName`|Nome do repositório de certificados.|
|`storeLocation`|O local do repositório de certificados.|

|Opção|Descrição|
|------------|-----------------|
|`/n <` *subjectName* `>`|Especifica o nome da entidade do certificado.|
|`/t <` *thumbprint* `>`|Especifica a impressão digital do certificado. Use Certmgr.exe para recuperar a impressão digital do certificado.|
|`/f`|Gera o nome de arquivo.|
|`/d`|Gera apenas o diretório.|
|`/a`|Gera o nome de arquivo absoluto.|

## <a name="examples"></a>Exemplos

O comando a seguir recupera a chave privada para John Doe:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

O comando a seguir recupera a chave privada para o computador local:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```