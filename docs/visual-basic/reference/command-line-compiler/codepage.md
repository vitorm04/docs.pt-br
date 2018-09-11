---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: fda75383435fdff718d1d50bc8583afc9858e7e2
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276481"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`id`|Necessário. O compilador usa a página de código especificada pelo `id` para interpretar a codificação dos arquivos de origem.|  
  
## <a name="remarks"></a>Comentários  
 Para compilar o código-fonte salvo com uma codificação específica, você pode usar `-codepage` para especificar qual página de código deve ser usada. O `-codepage` opção se aplica a todos os arquivos de código-fonte na compilação. Para obter mais informações, consulte [codificação de caracteres no .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 O `-codepage` opção não será necessária se os arquivos de código-fonte foram salvos com a página de código ANSI atual, Unicode ou UTF-8 com uma assinatura. O Visual Studio salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação na **Encoding** caixa de diálogo. O Visual Studio usa o **Encoding** caixa de diálogo para abrir arquivos de código-fonte salvos com uma página de código diferente.  
  
> [!NOTE]
>  O `-codepage` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
