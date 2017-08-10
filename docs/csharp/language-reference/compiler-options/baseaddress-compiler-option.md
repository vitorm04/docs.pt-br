---
title: "-baseaddress (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dllbase
dev_langs:
- CSharp
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
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
ms.openlocfilehash: 91193ae794957b5045a225614d6322e86d18d459
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (opções do compilador C#)
A opção **/baseaddress** permite especificar o endereço básico preferido em que uma DLL será carregada. Para obter mais informações sobre quando e por que usar essa opção, consulte [Melhorando o Tempo de Inicialização do Aplicativo](http://go.microsoft.com/fwlink/?LinkId=107043) e [Log da Web do Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 O endereço básico da DLL. Esse endereço pode ser especificado como um número decimal, hexadecimal ou octal.  
  
## <a name="remarks"></a>Comentários  
 O endereço básico padrão de uma DLL é definido pelo Common Language Runtime do .NET Framework.  
  
 Lembre-se de que a palavra de ordem inferior nesse endereço será arredondada. Por exemplo, se 0x11110001 for especificado, será arredondado para 0x11110000.  
  
 Para concluir o processo de assinatura de uma DLL, use SN.EXE com a opção -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Endereço Básico de DLL**.  
  
     Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)

