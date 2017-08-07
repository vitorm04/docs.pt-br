---
title: "-highentropyva (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /highentropyva
dev_langs:
- CSharp
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4cb21c109fc33a30da016fd6a42285a3a3da02e2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="highentropyva-c-compiler-options"></a>/highentropyva (opções do compilador C#)
A opção do compilador **/highentropyva** informa ao kernel do Windows se um determinado executável dá suporte à ASLR (Address Space Layout Randomization) de alta entropia.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Essa opção especifica que um executável de 64 bits ou um executável que está marcado com a opção do compilador [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) dá suporte a um espaço de endereço virtual de alta entropia. A opção está desabilitada por padrão. Use **/highentropyva+** ou **/highentropyva** para habilitá-la.  
  
## <a name="remarks"></a>Comentários  
 A opção **/highentropyva** permite que as versões compatíveis do kernel do Windows usem níveis mais altos de entropia ao randomizar o layout do espaço de endereço de um processo, como parte da ASLR. O uso de níveis mais altos de entropia significa que um número maior de endereços pode ser alocado para regiões de memória como pilhas e heaps. Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.  
  
 Quando a opção do compilador **/highentropyva** for especificada, o executável de destino e todos os módulos dos quais ele depende devem ser capazes de manipular valores de ponteiro que são maiores que 4 gigabytes (GB) quando eles estiverem em execução como um processo de 64 bits.

