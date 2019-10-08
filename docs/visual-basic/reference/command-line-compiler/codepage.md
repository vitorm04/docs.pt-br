---
title: -CodePage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: e4cdc27ab021fe055f157b78946538f2b76870e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002364"
---
# <a name="-codepage-visual-basic"></a>-CodePage (Visual Basic)
Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`id`|Necessário. O compilador usa a página de código especificada por `id` para interpretar a codificação dos arquivos de origem.|  
  
## <a name="remarks"></a>Comentários  
 Para compilar o código-fonte salvo com uma codificação específica, você pode usar `-codepage` para especificar qual página de código deve ser usada. A opção `-codepage` se aplica a todos os arquivos de código-fonte em sua compilação. Para obter mais informações, consulte [codificação de caracteres no .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 A opção `-codepage` não será necessária se os arquivos de código-fonte tiverem sido salvos usando a página de código ANSI atual, o Unicode ou o UTF-8 com uma assinatura. O Visual Studio salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação na caixa de diálogo **codificação** . O Visual Studio usa a caixa de diálogo **codificação** para abrir arquivos de código-fonte salvos com uma página de código diferente.  
  
> [!NOTE]
> A opção `-codepage` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
