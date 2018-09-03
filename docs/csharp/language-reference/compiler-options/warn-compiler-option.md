---
title: -warn (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 14656fa25ea1d01339bd63efb999e938e1243db8
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331935"
---
# <a name="-warn-c-compiler-options"></a>-warn (opções do compilador C#)
A opção **-warn** especifica o nível de aviso a ser exibido pelo compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 O nível de aviso que você deseja que seja exibido para a compilação: números mais baixos mostram apenas avisos de gravidade alta; números mais altos mostram mais avisos. Os valores válidos vão de 0 a 4:  
  
|Nível de aviso|Significado|  
|-------------------|-------------|  
|0|Desativa a emissão de todas as mensagens de aviso.|  
|1|Exibe mensagens de aviso graves.|  
|2|Exibe os avisos do nível 1 e mais alguns avisos menos graves, como avisos sobre membros de classe ocultos.|  
|3|Exibe os avisos do nível 2 e mais alguns avisos menos graves, como avisos sobre expressões que sempre resultam em `true` ou `false`.|  
|4 (o padrão)|Exibe todos os avisos do nível 3 e também avisos informativos.|  
  
## <a name="remarks"></a>Comentários  
 Para obter informações sobre um erro ou aviso, você pode procurar o código de erro no Índice da Ajuda. Para outras maneiras de se obter informações sobre um erro ou aviso, consulte [Erros do compilador do C#](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) para tratar todos os avisos como erros. Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) para desabilitar determinados avisos.  
  
 **-w** é a forma abreviada de **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Modifique a propriedade **Nível de Aviso**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Exemplo  
 Compilar `in.cs` e fazer com que o compilador exiba somente avisos de nível 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Consulte também  

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
