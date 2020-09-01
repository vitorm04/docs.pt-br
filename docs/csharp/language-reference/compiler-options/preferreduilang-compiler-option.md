---
description: -preferreduilang (opções do compilador C#)
title: -preferreduilang (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: f68652e910651ab5c4184376d9eb7729303382d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124845"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (opções do compilador C#)
Usando a opção do compilador `-preferreduilang`, é possível especificar o idioma em que o compilador C# exibe a saída, como mensagens de erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>Argumentos  
 `language`  
 O [nome do idioma](/windows/desktop/Intl/language-names) do idioma a ser usado para a saída do compilador.  
  
## <a name="remarks"></a>Comentários  
 É possível usar a opção do compilador `-preferreduilang` para especificar o idioma que você deseja que o compilador C# use para mensagens de erro e outras saídas de linha de comando. Se o pacote de idiomas do idioma não estiver instalado, a configuração de idioma do sistema operacional será usada e nenhum erro será relatado.  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Confira também

- [Opções do compilador C#](./index.md)
