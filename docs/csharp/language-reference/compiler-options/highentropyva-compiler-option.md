---
title: "-highentropyva (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d0b9a7a53545623ae5d5692b52973744adbcc299
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (opções do compilador C#)
A opção do compilador **-highentropyva** informa ao kernel do Windows se um determinado executável é compatível com ASLR (Address Space Layout Randomization) de alta entropia.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Essa opção especifica que um executável de 64 bits ou um executável que está marcado com a opção do compilador [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) é compatível com um espaço de endereço virtual de alta entropia. A opção está desabilitada por padrão. Use **-highentropyva+** ou **-highentropyva** para habilitá-la.  
  
## <a name="remarks"></a>Comentários  
 A opção **-highentropyva** permite que as versões compatíveis do kernel do Windows usem níveis mais altos de entropia ao randomizar o layout do espaço de endereço de um processo como parte da ASLR. O uso de níveis mais altos de entropia significa que um número maior de endereços pode ser alocado para regiões de memória como pilhas e heaps. Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.  
  
 Quando a opção do compilador **-highentropyva** é especificada, o executável de destino e todos os módulos dos quais ele depende devem ser capazes de manipular valores de ponteiro que sejam maiores que 4 GB (gigabytes) quando eles estiverem em execução como um processo de 64 bits.
