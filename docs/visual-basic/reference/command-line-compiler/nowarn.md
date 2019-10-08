---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005404"
---
# <a name="-nowarn"></a>-nowarn
Suprime a capacidade do compilador de gerar avisos.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`numberList`|Opcional. Lista delimitada por vírgulas dos números de ID de aviso que o compilador deve suprimir. Se as IDs de aviso não forem especificadas, todos os avisos serão suprimidos.|  
  
## <a name="remarks"></a>Comentários  
 A opção `-nowarn` faz com que o compilador não gere avisos. Para suprimir um aviso individual, forneça a ID de aviso à opção `-nowarn` após os dois-pontos. Separe vários números de aviso com vírgulas.  
  
 Você precisa especificar apenas a parte numérica do identificador de aviso. Por exemplo, se você quiser suprimir BC42024, o aviso para variáveis locais não usadas, especifique `-nowarn:42024`.  
  
 Para obter mais informações sobre os números de identificação de aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Para definir-nowarn no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Marque a caixa de seleção **desabilitar todos os avisos** para desabilitar todos os avisos.<br />     - ou -<br />     Para desabilitar um aviso específico, clique em **nenhum** na lista suspensa adjacente ao aviso.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e não exibe nenhum aviso.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
