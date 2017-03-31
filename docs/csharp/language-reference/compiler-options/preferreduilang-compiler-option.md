---
title: "-preferreduilang (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
dev_langs:
- CSharp
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 30585b6df0a7acbc109d386efe0e311b1625342d
ms.lasthandoff: 03/13/2017

---
# <a name="preferreduilang-c-compiler-options"></a>/preferreduilang (opções do compilador C#)
Usando a opção do compilador `/preferreduilang`, é possível especificar o idioma em que o compilador C# exibe a saída, como mensagens de erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/preferreduilang: language  
```  
  
## <a name="arguments"></a>Arguments  
 `language`  
 O [nome do idioma](http://go.microsoft.com/fwlink/p/?LinkId=236992) do idioma a ser usado para a saída do compilador.  
  
## <a name="remarks"></a>Comentários  
 É possível usar a opção do compilador `/preferreduilang` para especificar o idioma que você deseja que o compilador C# use para mensagens de erro e outras saídas de linha de comando. Se o pacote de idiomas do idioma não estiver instalado, a configuração de idioma do sistema operacional será usada e nenhum erro será relatado.  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>Requisitos  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
