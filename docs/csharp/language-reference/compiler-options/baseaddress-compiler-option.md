---
title: "/baseaddress (Opções do Compilador C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6c29d3b4b1ef2f92f246a9432cab5aef855691dd
ms.lasthandoff: 03/13/2017

---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (opções do compilador C#)
A opção **/baseaddress** permite especificar o endereço básico preferido em que uma DLL será carregada. Para obter mais informações sobre quando e por que usar essa opção, consulte [Melhorando o Tempo de Inicialização do Aplicativo](http://go.microsoft.com/fwlink/?LinkId=107043) e [Log da Web do Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
     Para definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
