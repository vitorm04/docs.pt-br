---
title: "Mitigação: novo compilador JIT de 64 bits | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 994da1622246d09930fa9b74d6debac4f7a24b5b
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Mitigação: novo compilador JIT de 64 bits
A partir do .NET Framework 4.6, o tempo de execução inclui um novo compilador JIT de 64 bits para compilação just-in-time. Essa alteração não afeta a compilação com o compilador JIT de 32 bits.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Comportamento ou exceções inesperadas  
 Em alguns casos, a compilação com o novo compilador JIT de 64 bits resulta em uma exceção de tempo de execução ou em um comportamento não observado durante a execução do código compilado pelo compilador JIT de 64 bits mais antigo. Os diferenças conhecidas incluem o seguinte:  
  
> [!IMPORTANT]
>  Todos esses problemas conhecidos foram resolvidos no novo compilador de 64 bits lançado com o .NET Framework 4.6.2. A maioria também foi resolvida nas versões de serviço do .NET Framework 4.6 e 4.6.1, incluídos com o Windows Update. Você pode eliminar esses problemas garantindo que sua versão do Windows esteja atualizada, ou atualizando para o .NET Framework 4.6.2.  
  
-   Sob certas condições, uma operação de conversão unboxing pode gerar uma <xref:System.NullReferenceException> em compilações de Versão com a otimização ativada.  
  
-   Em alguns casos, a execução do código de produção em um corpo de método grande pode gerar <xref:System.StackOverflowException>.  
  
-   Sob certas condições, as estruturas passadas para um método são tratadas como tipos de referência em vez de tipos de valor em compilações de Versão. Um das manifestações desse problema é que os itens individuais em uma coleção aparecem em uma ordem inesperada.  
  
-   Sob determinadas condições, a comparação de valores <xref:System.UInt16> com seu conjunto de bits alto será incorreta se a otimização estiver habilitada.  
  
-   Sob certas condições, especialmente ao inicializar uma matriz de valores, a inicialização da memória pela instrução IL <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=fullName> pode inicializar a memória com um valor incorreto. Isso pode resultar em uma saída incorreta ou uma exceção sem tratamento.  
  
-   Sob certas condições raras, um teste de bits condicional pode retornar o valor <xref:System.Boolean> incorreto ou gerar uma exceção se as otimizações do compilador estiverem habilitadas.  
  
-   Sob certas condições, se uma instrução `if` for usada para testar uma condição antes de entrar em um bloco `try`, e na saída do bloco `try`, e a mesma condição for avaliada no bloco `catch` ou `finally`, o novo compilador JIT de 64 bits removerá a condição `if` do bloco `catch` ou `finally` durante a otimização do código. Como resultado, o código dentro da instrução `if` no bloco `catch` ou `finally` será executado incondicionalmente.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Mitigação dos problemas conhecidos  
 Se você encontrar os problemas listados acima, solucione-os seguindo um destes procedimentos:  
  
-   Atualizar para o .NET Framework 4.6.2. O novo compilador de 64 bits incluído com o .NET Framework 4.6.2 resolve cada um desses problemas conhecidos.  
  
-   Verifique se a sua versão do Windows está atualizada executando o Windows Update. Atualizações de serviço para o .NET Framework 4.6 e 4.6.1 resolvem cada um desses problemas, exceto a <xref:System.NullReferenceException>em uma operação de conversão unboxing.  
  
-   Compilar com o compilador JIT de 64 bits mais antigo. Veja a seção [Mitigação de outros problemas](#Other) para saber mais sobre como fazer isso.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Mitigação de outros problemas  
 Se você encontrar qualquer outra diferença de comportamento entre o código compilado com o compilador de 64 bits mais antigo e o novo compilador JIT de 64 bits, ou entre as versões de depuração e de versão de seu aplicativo, ambas compiladas com o novo compilador JIT de 64 bits, faça o seguinte para compilar seu aplicativo com o compilador JIT de 64 bits mais antigo:  
  
-   Adicione a cada aplicativo o elemento [\<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) ao arquivo de configuração do aplicativo. Veja a seguir como desabilitar a compilação com o novo compilador JIT de 64 bits e usar, em vez disso, o compilador JIT de 64 bits herdado.  
  
    ```xml  
  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJIT enabled="1" />  
        </runtime>  
    </configuration>  
  
    ```  
  
-   Adicione a cada usuário um valor `REG_DWORD` denominado `useLegacyJit` para a chave `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` do Registro. Um valor 1 habilita o compilador JIT de 64 bits herdado; um valor 0 o desabilita e habilita o novo compilador JIT de 64 bits.  
  
-   Adicione a cada máquina um valor `REG_DWORD` denominado `useLegacyJit` para a chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` do Registro. Um valor 1 habilita o compilador JIT de 64 bits herdado; um valor 0 o desabilita e habilita o novo compilador JIT de 64 bits.  
  
 Avise-nos sobre o problema relatando um bug no [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)   
 [\<Elemento useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
