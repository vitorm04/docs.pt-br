---
title: Encontrar ferramenta de chave privada (FindPrivateKey.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Encontrar ferramenta de chave privada (FindPrivateKey.exe)
Essa ferramenta de linha de comando pode ser usada para recuperar uma chave privada de um repositório de certificados. Por exemplo, FindPrivateKey.exe pode ser usado para localizar o local e o nome do arquivo da chave privado associado com um certificado x. 509 específico no repositório de certificados.  
  
> [!IMPORTANT]
>  A ferramenta FindPrivateKey é enviada como um exemplo do WCF. Para obter mais informações sobre onde encontrar o exemplo e como criá-lo, consulte  
  
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
|`/n <`*subjectName*`>`|Especifica o nome da entidade do certificado.|  
|`/t <`*impressão digital*`>`|Especifica a impressão digital do certificado. Use Certmgr.exe para recuperar a impressão digital do certificado.|  
|`/f`|Gera o nome de arquivo.|  
|`/d`|Gera o diretório somente.|  
|`/a`|Gera o nome de arquivo absoluto.|  
  
## <a name="examples"></a>Exemplos  
 O comando a seguir recupera a chave privada para John Doe.  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 O comando a seguir recupera a chave privada para a máquina local.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
