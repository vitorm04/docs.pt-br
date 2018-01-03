---
title: "Coleções de esquema ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="f1a88-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="f1a88-102">ODBC Schema Collections</span></span>
<span data-ttu-id="f1a88-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="f1a88-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="f1a88-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="f1a88-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="f1a88-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="f1a88-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f1a88-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="f1a88-106">Tables</span></span>  
  
-   <span data-ttu-id="f1a88-107">Índices</span><span class="sxs-lookup"><span data-stu-id="f1a88-107">Indexes</span></span>  
  
-   <span data-ttu-id="f1a88-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="f1a88-108">Columns</span></span>  
  
-   <span data-ttu-id="f1a88-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1a88-109">Procedures</span></span>  
  
-   <span data-ttu-id="f1a88-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f1a88-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f1a88-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f1a88-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f1a88-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="f1a88-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f1a88-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="f1a88-113">Tables and Views</span></span>  
  
|<span data-ttu-id="f1a88-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-114">ColumnName</span></span>|<span data-ttu-id="f1a88-115">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-116">TABLE_CAT</span></span>|<span data-ttu-id="f1a88-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-117">String</span></span>|  
|<span data-ttu-id="f1a88-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-118">TABLE_SCHEM</span></span>|<span data-ttu-id="f1a88-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-119">String</span></span>|  
|<span data-ttu-id="f1a88-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-120">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-121">String</span></span>|  
|<span data-ttu-id="f1a88-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-122">TABLE_TYPE</span></span>|<span data-ttu-id="f1a88-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-123">String</span></span>|  
|<span data-ttu-id="f1a88-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-124">REMARKS</span></span>|<span data-ttu-id="f1a88-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f1a88-126">Índices</span><span class="sxs-lookup"><span data-stu-id="f1a88-126">Indexes</span></span>  
  
|<span data-ttu-id="f1a88-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-127">ColumnName</span></span>|<span data-ttu-id="f1a88-128">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-129">TABLE_CAT</span></span>|<span data-ttu-id="f1a88-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-130">String</span></span>|  
|<span data-ttu-id="f1a88-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-131">TABLE_SCHEM</span></span>|<span data-ttu-id="f1a88-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-132">String</span></span>|  
|<span data-ttu-id="f1a88-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-133">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-134">String</span></span>|  
|<span data-ttu-id="f1a88-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="f1a88-135">NON_UNIQUE</span></span>|<span data-ttu-id="f1a88-136">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-136">Int16</span></span>|  
|<span data-ttu-id="f1a88-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="f1a88-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-138">String</span></span>|  
|<span data-ttu-id="f1a88-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-139">INDEX_NAME</span></span>|<span data-ttu-id="f1a88-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-140">String</span></span>|  
|<span data-ttu-id="f1a88-141">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="f1a88-141">TYPE</span></span>|<span data-ttu-id="f1a88-142">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-142">Int16</span></span>|  
|<span data-ttu-id="f1a88-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-144">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-144">Int16</span></span>|  
|<span data-ttu-id="f1a88-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-145">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-146">String</span></span>|  
|<span data-ttu-id="f1a88-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="f1a88-147">ASC_OR_DESC</span></span>|<span data-ttu-id="f1a88-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-148">String</span></span>|  
|<span data-ttu-id="f1a88-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="f1a88-149">CARDINATLITY</span></span>|<span data-ttu-id="f1a88-150">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-150">Int32</span></span>|  
|<span data-ttu-id="f1a88-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="f1a88-151">PAGES</span></span>|<span data-ttu-id="f1a88-152">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-152">Int32</span></span>|  
|<span data-ttu-id="f1a88-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-153">FILTER_CONDITION</span></span>|<span data-ttu-id="f1a88-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-154">String</span></span>|  
|<span data-ttu-id="f1a88-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1a88-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f1a88-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-156">String</span></span>|  
|<span data-ttu-id="f1a88-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-158">Byte</span><span class="sxs-lookup"><span data-stu-id="f1a88-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f1a88-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="f1a88-159">Columns</span></span>  
  
|<span data-ttu-id="f1a88-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-160">ColumnName</span></span>|<span data-ttu-id="f1a88-161">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-162">TABLE_CAT</span></span>|<span data-ttu-id="f1a88-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-163">String</span></span>|  
|<span data-ttu-id="f1a88-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-164">TABLE_SCHEM</span></span>|<span data-ttu-id="f1a88-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-165">String</span></span>|  
|<span data-ttu-id="f1a88-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-166">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-167">String</span></span>|  
|<span data-ttu-id="f1a88-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-168">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-169">String</span></span>|  
|<span data-ttu-id="f1a88-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-170">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-171">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-171">Int16</span></span>|  
|<span data-ttu-id="f1a88-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-172">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-173">String</span></span>|  
|<span data-ttu-id="f1a88-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f1a88-174">COLUMN_SIZE</span></span>|<span data-ttu-id="f1a88-175">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-175">Int32</span></span>|  
|<span data-ttu-id="f1a88-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="f1a88-177">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-177">Int32</span></span>|  
|<span data-ttu-id="f1a88-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f1a88-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f1a88-179">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-179">Int16</span></span>|  
|<span data-ttu-id="f1a88-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f1a88-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f1a88-181">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-181">Int16</span></span>|  
|<span data-ttu-id="f1a88-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-182">NULLABLE</span></span>|<span data-ttu-id="f1a88-183">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-183">Int16</span></span>|  
|<span data-ttu-id="f1a88-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-184">REMARKS</span></span>|<span data-ttu-id="f1a88-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-185">String</span></span>|  
|<span data-ttu-id="f1a88-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f1a88-186">COLUMN_DEF</span></span>|<span data-ttu-id="f1a88-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-187">String</span></span>|  
|<span data-ttu-id="f1a88-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-189">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-189">Int16</span></span>|  
|<span data-ttu-id="f1a88-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f1a88-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f1a88-191">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-191">Int16</span></span>|  
|<span data-ttu-id="f1a88-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f1a88-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-193">Int32</span></span>|  
|<span data-ttu-id="f1a88-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-195">Int32</span></span>|  
|<span data-ttu-id="f1a88-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f1a88-196">IS_NULLABLE</span></span>|<span data-ttu-id="f1a88-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-197">String</span></span>|  
|<span data-ttu-id="f1a88-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1a88-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f1a88-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-199">String</span></span>|  
|<span data-ttu-id="f1a88-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1a88-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f1a88-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-201">String</span></span>|  
|<span data-ttu-id="f1a88-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-203">Byte</span><span class="sxs-lookup"><span data-stu-id="f1a88-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f1a88-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1a88-204">Procedures</span></span>  
  
|<span data-ttu-id="f1a88-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-205">ColumnName</span></span>|<span data-ttu-id="f1a88-206">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="f1a88-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-208">String</span></span>|  
|<span data-ttu-id="f1a88-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f1a88-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-210">String</span></span>|  
|<span data-ttu-id="f1a88-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-212">String</span></span>|  
|<span data-ttu-id="f1a88-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f1a88-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f1a88-214">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-214">Int32</span></span>|  
|<span data-ttu-id="f1a88-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f1a88-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f1a88-216">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-216">Int32</span></span>|  
|<span data-ttu-id="f1a88-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f1a88-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f1a88-218">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-218">Int32</span></span>|  
|<span data-ttu-id="f1a88-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-219">REMARKS</span></span>|<span data-ttu-id="f1a88-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-220">String</span></span>|  
|<span data-ttu-id="f1a88-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f1a88-222">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f1a88-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f1a88-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f1a88-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-224">ColumnName</span></span>|<span data-ttu-id="f1a88-225">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="f1a88-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-227">String</span></span>|  
|<span data-ttu-id="f1a88-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f1a88-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-229">String</span></span>|  
|<span data-ttu-id="f1a88-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-231">String</span></span>|  
|<span data-ttu-id="f1a88-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-232">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-233">String</span></span>|  
|<span data-ttu-id="f1a88-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-234">COLUMN_TYPE</span></span>|<span data-ttu-id="f1a88-235">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-235">Int16</span></span>|  
|<span data-ttu-id="f1a88-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-236">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-237">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-237">Int16</span></span>|  
|<span data-ttu-id="f1a88-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-238">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-239">String</span></span>|  
|<span data-ttu-id="f1a88-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f1a88-240">COLUMN_SIZE</span></span>|<span data-ttu-id="f1a88-241">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-241">Int32</span></span>|  
|<span data-ttu-id="f1a88-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="f1a88-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-243">Int32</span></span>|  
|<span data-ttu-id="f1a88-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f1a88-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f1a88-245">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-245">Int16</span></span>|  
|<span data-ttu-id="f1a88-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f1a88-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f1a88-247">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-247">Int16</span></span>|  
|<span data-ttu-id="f1a88-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-248">NULLABLE</span></span>|<span data-ttu-id="f1a88-249">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-249">Int16</span></span>|  
|<span data-ttu-id="f1a88-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-250">REMARKS</span></span>|<span data-ttu-id="f1a88-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-251">String</span></span>|  
|<span data-ttu-id="f1a88-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f1a88-252">COLUMN_DEF</span></span>|<span data-ttu-id="f1a88-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-253">String</span></span>|  
|<span data-ttu-id="f1a88-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-255">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-255">Int16</span></span>|  
|<span data-ttu-id="f1a88-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f1a88-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f1a88-257">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-257">Int16</span></span>|  
|<span data-ttu-id="f1a88-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f1a88-259">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-259">Int32</span></span>|  
|<span data-ttu-id="f1a88-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-261">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-261">Int32</span></span>|  
|<span data-ttu-id="f1a88-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f1a88-262">IS_NULLABLE</span></span>|<span data-ttu-id="f1a88-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-263">String</span></span>|  
|<span data-ttu-id="f1a88-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1a88-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f1a88-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-265">String</span></span>|  
|<span data-ttu-id="f1a88-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1a88-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f1a88-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-267">String</span></span>|  
|<span data-ttu-id="f1a88-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-269">Byte</span><span class="sxs-lookup"><span data-stu-id="f1a88-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f1a88-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f1a88-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f1a88-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-271">ColumnName</span></span>|<span data-ttu-id="f1a88-272">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="f1a88-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-274">String</span></span>|  
|<span data-ttu-id="f1a88-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f1a88-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-276">String</span></span>|  
|<span data-ttu-id="f1a88-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-278">String</span></span>|  
|<span data-ttu-id="f1a88-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-279">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-280">String</span></span>|  
|<span data-ttu-id="f1a88-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-281">COLUMN_TYPE</span></span>|<span data-ttu-id="f1a88-282">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-282">Int16</span></span>|  
|<span data-ttu-id="f1a88-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-283">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-284">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-284">Int16</span></span>|  
|<span data-ttu-id="f1a88-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-285">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-286">String</span></span>|  
|<span data-ttu-id="f1a88-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f1a88-287">COLUMN_SIZE</span></span>|<span data-ttu-id="f1a88-288">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-288">Int32</span></span>|  
|<span data-ttu-id="f1a88-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="f1a88-290">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-290">Int32</span></span>|  
|<span data-ttu-id="f1a88-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f1a88-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f1a88-292">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-292">Int16</span></span>|  
|<span data-ttu-id="f1a88-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f1a88-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f1a88-294">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-294">Int16</span></span>|  
|<span data-ttu-id="f1a88-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-295">NULLABLE</span></span>|<span data-ttu-id="f1a88-296">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-296">Int16</span></span>|  
|<span data-ttu-id="f1a88-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-297">REMARKS</span></span>|<span data-ttu-id="f1a88-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-298">String</span></span>|  
|<span data-ttu-id="f1a88-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f1a88-299">COLUMN_DEF</span></span>|<span data-ttu-id="f1a88-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-300">String</span></span>|  
|<span data-ttu-id="f1a88-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-302">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-302">Int16</span></span>|  
|<span data-ttu-id="f1a88-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f1a88-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f1a88-304">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-304">Int16</span></span>|  
|<span data-ttu-id="f1a88-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f1a88-306">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-306">Int32</span></span>|  
|<span data-ttu-id="f1a88-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-308">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-308">Int32</span></span>|  
|<span data-ttu-id="f1a88-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f1a88-309">IS_NULLABLE</span></span>|<span data-ttu-id="f1a88-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-310">String</span></span>|  
|<span data-ttu-id="f1a88-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f1a88-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f1a88-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-312">String</span></span>|  
|<span data-ttu-id="f1a88-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f1a88-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f1a88-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-314">String</span></span>|  
|<span data-ttu-id="f1a88-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-316">Byte</span><span class="sxs-lookup"><span data-stu-id="f1a88-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="f1a88-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="f1a88-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="f1a88-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="f1a88-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f1a88-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="f1a88-319">Tables</span></span>  
  
-   <span data-ttu-id="f1a88-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="f1a88-320">Columns</span></span>  
  
-   <span data-ttu-id="f1a88-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1a88-321">Procedures</span></span>  
  
-   <span data-ttu-id="f1a88-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f1a88-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f1a88-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f1a88-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f1a88-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="f1a88-324">Views</span></span>  
  
-   <span data-ttu-id="f1a88-325">Índices</span><span class="sxs-lookup"><span data-stu-id="f1a88-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f1a88-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="f1a88-326">Tables and Views</span></span>  
  
|<span data-ttu-id="f1a88-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-327">ColumnName</span></span>|<span data-ttu-id="f1a88-328">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-330">String</span></span>|  
|<span data-ttu-id="f1a88-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-331">TABLE_OWNER</span></span>|<span data-ttu-id="f1a88-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-332">String</span></span>|  
|<span data-ttu-id="f1a88-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-333">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-334">String</span></span>|  
|<span data-ttu-id="f1a88-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-335">TABLE_TYPE</span></span>|<span data-ttu-id="f1a88-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-336">String</span></span>|  
|<span data-ttu-id="f1a88-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-337">REMARKS</span></span>|<span data-ttu-id="f1a88-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f1a88-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="f1a88-339">Columns</span></span>  
  
|<span data-ttu-id="f1a88-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-340">ColumnName</span></span>|<span data-ttu-id="f1a88-341">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-343">String</span></span>|  
|<span data-ttu-id="f1a88-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-344">TABLE_OWNER</span></span>|<span data-ttu-id="f1a88-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-345">String</span></span>|  
|<span data-ttu-id="f1a88-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-346">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-347">String</span></span>|  
|<span data-ttu-id="f1a88-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-348">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-349">String</span></span>|  
|<span data-ttu-id="f1a88-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-350">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-351">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-351">Int16</span></span>|  
|<span data-ttu-id="f1a88-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-352">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-353">String</span></span>|  
|<span data-ttu-id="f1a88-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="f1a88-354">PRECISION</span></span>|<span data-ttu-id="f1a88-355">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-355">Int32</span></span>|  
|<span data-ttu-id="f1a88-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="f1a88-356">LENGTH</span></span>|<span data-ttu-id="f1a88-357">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-357">Int32</span></span>|  
|<span data-ttu-id="f1a88-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="f1a88-358">SCALE</span></span>|<span data-ttu-id="f1a88-359">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-359">Int16</span></span>|  
|<span data-ttu-id="f1a88-360">BASE</span><span class="sxs-lookup"><span data-stu-id="f1a88-360">RADIX</span></span>|<span data-ttu-id="f1a88-361">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-361">Int16</span></span>|  
|<span data-ttu-id="f1a88-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-362">NULLABLE</span></span>|<span data-ttu-id="f1a88-363">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-363">Int16</span></span>|  
|<span data-ttu-id="f1a88-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-364">REMARKS</span></span>|<span data-ttu-id="f1a88-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-365">String</span></span>|  
|<span data-ttu-id="f1a88-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-367">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f1a88-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1a88-368">Procedures</span></span>  
  
|<span data-ttu-id="f1a88-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-369">ColumnName</span></span>|<span data-ttu-id="f1a88-370">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-372">String</span></span>|  
|<span data-ttu-id="f1a88-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f1a88-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-374">String</span></span>|  
|<span data-ttu-id="f1a88-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-376">String</span></span>|  
|<span data-ttu-id="f1a88-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f1a88-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f1a88-378">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-378">Int16</span></span>|  
|<span data-ttu-id="f1a88-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f1a88-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f1a88-380">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-380">Int16</span></span>|  
|<span data-ttu-id="f1a88-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f1a88-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f1a88-382">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-382">Int16</span></span>|  
|<span data-ttu-id="f1a88-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-383">REMARKS</span></span>|<span data-ttu-id="f1a88-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-384">String</span></span>|  
|<span data-ttu-id="f1a88-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f1a88-386">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f1a88-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f1a88-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f1a88-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-388">ColumnName</span></span>|<span data-ttu-id="f1a88-389">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-391">String</span></span>|  
|<span data-ttu-id="f1a88-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f1a88-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-393">String</span></span>|  
|<span data-ttu-id="f1a88-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-395">String</span></span>|  
|<span data-ttu-id="f1a88-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-396">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-397">String</span></span>|  
|<span data-ttu-id="f1a88-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-398">COLUMN_TYPE</span></span>|<span data-ttu-id="f1a88-399">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-399">Int16</span></span>|  
|<span data-ttu-id="f1a88-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-400">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-401">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-401">Int16</span></span>|  
|<span data-ttu-id="f1a88-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-402">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-403">String</span></span>|  
|<span data-ttu-id="f1a88-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="f1a88-404">PRECISION</span></span>|<span data-ttu-id="f1a88-405">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-405">Int32</span></span>|  
|<span data-ttu-id="f1a88-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="f1a88-406">LENGTH</span></span>|<span data-ttu-id="f1a88-407">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-407">Int32</span></span>|  
|<span data-ttu-id="f1a88-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="f1a88-408">SCALE</span></span>|<span data-ttu-id="f1a88-409">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-409">Int16</span></span>|  
|<span data-ttu-id="f1a88-410">BASE</span><span class="sxs-lookup"><span data-stu-id="f1a88-410">RADIX</span></span>|<span data-ttu-id="f1a88-411">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-411">Int16</span></span>|  
|<span data-ttu-id="f1a88-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-412">NULLABLE</span></span>|<span data-ttu-id="f1a88-413">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-413">Int16</span></span>|  
|<span data-ttu-id="f1a88-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-414">REMARKS</span></span>|<span data-ttu-id="f1a88-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-415">String</span></span>|  
|<span data-ttu-id="f1a88-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="f1a88-416">OVERLOAD</span></span>|<span data-ttu-id="f1a88-417">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-417">Int32</span></span>|  
|<span data-ttu-id="f1a88-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-419">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="f1a88-420">Driver ODBC do Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="f1a88-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="f1a88-421">O Driver de ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="f1a88-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f1a88-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="f1a88-422">Tables</span></span>  
  
-   <span data-ttu-id="f1a88-423">Índices</span><span class="sxs-lookup"><span data-stu-id="f1a88-423">Indexes</span></span>  
  
-   <span data-ttu-id="f1a88-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="f1a88-424">Columns</span></span>  
  
-   <span data-ttu-id="f1a88-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1a88-425">Procedures</span></span>  
  
-   <span data-ttu-id="f1a88-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f1a88-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f1a88-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f1a88-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f1a88-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="f1a88-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="f1a88-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="f1a88-429">Tables and Views</span></span>  
  
|<span data-ttu-id="f1a88-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-430">ColumnName</span></span>|<span data-ttu-id="f1a88-431">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-433">String</span></span>|  
|<span data-ttu-id="f1a88-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-434">TABLE_OWNER</span></span>|<span data-ttu-id="f1a88-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-435">String</span></span>|  
|<span data-ttu-id="f1a88-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-436">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-437">String</span></span>|  
|<span data-ttu-id="f1a88-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-438">TABLE_TYPE</span></span>|<span data-ttu-id="f1a88-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-439">String</span></span>|  
|<span data-ttu-id="f1a88-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-440">REMARKS</span></span>|<span data-ttu-id="f1a88-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f1a88-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="f1a88-442">Columns</span></span>  
  
|<span data-ttu-id="f1a88-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-443">ColumnName</span></span>|<span data-ttu-id="f1a88-444">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-446">String</span></span>|  
|<span data-ttu-id="f1a88-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-447">TABLE_OWNER</span></span>|<span data-ttu-id="f1a88-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-448">String</span></span>|  
|<span data-ttu-id="f1a88-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-449">TABLE_NAME</span></span>|<span data-ttu-id="f1a88-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-450">String</span></span>|  
|<span data-ttu-id="f1a88-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-451">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-452">String</span></span>|  
|<span data-ttu-id="f1a88-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-453">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-454">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-454">Int16</span></span>|  
|<span data-ttu-id="f1a88-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-455">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-456">String</span></span>|  
|<span data-ttu-id="f1a88-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="f1a88-457">PRECISION</span></span>|<span data-ttu-id="f1a88-458">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-458">Int32</span></span>|  
|<span data-ttu-id="f1a88-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="f1a88-459">LENGTH</span></span>|<span data-ttu-id="f1a88-460">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-460">Int32</span></span>|  
|<span data-ttu-id="f1a88-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="f1a88-461">SCALE</span></span>|<span data-ttu-id="f1a88-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-462">Int16</span></span>|  
|<span data-ttu-id="f1a88-463">BASE</span><span class="sxs-lookup"><span data-stu-id="f1a88-463">RADIX</span></span>|<span data-ttu-id="f1a88-464">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-464">Int16</span></span>|  
|<span data-ttu-id="f1a88-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-465">NULLABLE</span></span>|<span data-ttu-id="f1a88-466">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-466">Int16</span></span>|  
|<span data-ttu-id="f1a88-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-467">REMARKS</span></span>|<span data-ttu-id="f1a88-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-468">String</span></span>|  
|<span data-ttu-id="f1a88-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-470">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f1a88-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1a88-471">Procedures</span></span>  
  
|<span data-ttu-id="f1a88-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-472">ColumnName</span></span>|<span data-ttu-id="f1a88-473">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-475">String</span></span>|  
|<span data-ttu-id="f1a88-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f1a88-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-477">String</span></span>|  
|<span data-ttu-id="f1a88-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-479">String</span></span>|  
|<span data-ttu-id="f1a88-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f1a88-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f1a88-481">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-481">Int16</span></span>|  
|<span data-ttu-id="f1a88-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f1a88-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f1a88-483">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-483">Int16</span></span>|  
|<span data-ttu-id="f1a88-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f1a88-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f1a88-485">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-485">Int16</span></span>|  
|<span data-ttu-id="f1a88-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-486">REMARKS</span></span>|<span data-ttu-id="f1a88-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-487">String</span></span>|  
|<span data-ttu-id="f1a88-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f1a88-489">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f1a88-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f1a88-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f1a88-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-491">ColumnName</span></span>|<span data-ttu-id="f1a88-492">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f1a88-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f1a88-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-494">String</span></span>|  
|<span data-ttu-id="f1a88-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1a88-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f1a88-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-496">String</span></span>|  
|<span data-ttu-id="f1a88-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-498">String</span></span>|  
|<span data-ttu-id="f1a88-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-499">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-500">String</span></span>|  
|<span data-ttu-id="f1a88-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-501">COLUMN_TYPE</span></span>|<span data-ttu-id="f1a88-502">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-502">Int16</span></span>|  
|<span data-ttu-id="f1a88-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-503">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-504">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-504">Int16</span></span>|  
|<span data-ttu-id="f1a88-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-505">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-506">String</span></span>|  
|<span data-ttu-id="f1a88-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="f1a88-507">PRECISION</span></span>|<span data-ttu-id="f1a88-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-508">Int32</span></span>|  
|<span data-ttu-id="f1a88-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="f1a88-509">LENGTH</span></span>|<span data-ttu-id="f1a88-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-510">Int32</span></span>|  
|<span data-ttu-id="f1a88-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="f1a88-511">SCALE</span></span>|<span data-ttu-id="f1a88-512">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-512">Int16</span></span>|  
|<span data-ttu-id="f1a88-513">BASE</span><span class="sxs-lookup"><span data-stu-id="f1a88-513">RADIX</span></span>|<span data-ttu-id="f1a88-514">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-514">Int16</span></span>|  
|<span data-ttu-id="f1a88-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-515">NULLABLE</span></span>|<span data-ttu-id="f1a88-516">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-516">Int16</span></span>|  
|<span data-ttu-id="f1a88-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-517">REMARKS</span></span>|<span data-ttu-id="f1a88-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-518">String</span></span>|  
|<span data-ttu-id="f1a88-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="f1a88-519">OVERLOAD</span></span>|<span data-ttu-id="f1a88-520">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-520">Int32</span></span>|  
|<span data-ttu-id="f1a88-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-522">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f1a88-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f1a88-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f1a88-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f1a88-524">ColumnName</span></span>|<span data-ttu-id="f1a88-525">DataType</span><span class="sxs-lookup"><span data-stu-id="f1a88-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f1a88-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f1a88-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="f1a88-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-527">String</span></span>|  
|<span data-ttu-id="f1a88-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f1a88-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f1a88-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-529">String</span></span>|  
|<span data-ttu-id="f1a88-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="f1a88-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-531">String</span></span>|  
|<span data-ttu-id="f1a88-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-532">COLUMN_NAME</span></span>|<span data-ttu-id="f1a88-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-533">String</span></span>|  
|<span data-ttu-id="f1a88-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-534">COLUMN_TYPE</span></span>|<span data-ttu-id="f1a88-535">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-535">Int16</span></span>|  
|<span data-ttu-id="f1a88-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-536">DATA_TYPE</span></span>|<span data-ttu-id="f1a88-537">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-537">Int16</span></span>|  
|<span data-ttu-id="f1a88-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f1a88-538">TYPE_NAME</span></span>|<span data-ttu-id="f1a88-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-539">String</span></span>|  
|<span data-ttu-id="f1a88-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f1a88-540">COLUMN_SIZE</span></span>|<span data-ttu-id="f1a88-541">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-541">Int32</span></span>|  
|<span data-ttu-id="f1a88-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="f1a88-543">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-543">Int32</span></span>|  
|<span data-ttu-id="f1a88-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f1a88-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f1a88-545">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-545">Int16</span></span>|  
|<span data-ttu-id="f1a88-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f1a88-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f1a88-547">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-547">Int16</span></span>|  
|<span data-ttu-id="f1a88-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="f1a88-548">NULLABLE</span></span>|<span data-ttu-id="f1a88-549">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-549">Int16</span></span>|  
|<span data-ttu-id="f1a88-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="f1a88-550">REMARKS</span></span>|<span data-ttu-id="f1a88-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-551">String</span></span>|  
|<span data-ttu-id="f1a88-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f1a88-552">COLUMN_DEF</span></span>|<span data-ttu-id="f1a88-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-553">String</span></span>|  
|<span data-ttu-id="f1a88-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f1a88-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f1a88-555">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-555">Int16</span></span>|  
|<span data-ttu-id="f1a88-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f1a88-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f1a88-557">Int16</span><span class="sxs-lookup"><span data-stu-id="f1a88-557">Int16</span></span>|  
|<span data-ttu-id="f1a88-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f1a88-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f1a88-559">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-559">Int32</span></span>|  
|<span data-ttu-id="f1a88-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f1a88-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="f1a88-561">Int32</span><span class="sxs-lookup"><span data-stu-id="f1a88-561">Int32</span></span>|  
|<span data-ttu-id="f1a88-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f1a88-562">IS_NULLABLE</span></span>|<span data-ttu-id="f1a88-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f1a88-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1a88-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1a88-564">See Also</span></span>  
 <span data-ttu-id="f1a88-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f1a88-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
