<%@ Control Language="C#" AutoEventWireup="true" CodeFile="wucOrder.ascx.cs" Inherits="UserControls_wucOrder" %>
<%@ Register src="~/UserControls/wucCustomerSearchReturnRecord.ascx" tagname="wucCustomerSearchReturnRecord" tagprefix="uc1" %>
<%@ Register src="~/UserControls/wucOrderSearchReturnRecord.ascx" tagname="wucOrderSearchReturnRecord" tagprefix="uc2" %>



<asp:UpdatePanel ID="upOrder" runat="server"> 
<ContentTemplate>

<script type="text/javascript" src='<%= System.Configuration.ConfigurationManager.AppSettings["WebPagePath"]%>/Scripts/UserControls/wucOrder.js<%= System.Configuration.ConfigurationManager.AppSettings["WebVersion"] %>'></script>
<script type="text/javascript" src='<%= System.Configuration.ConfigurationManager.AppSettings["WebPagePath"]%>/Scripts/UserControls/wucCustomerSearch.js<%= System.Configuration.ConfigurationManager.AppSettings["WebVersion"] %>'></script>
<script type="text/javascript" src='<%= System.Configuration.ConfigurationManager.AppSettings["WebPagePath"]%>/Scripts/UserControls/wucOrderSearch.js<%= System.Configuration.ConfigurationManager.AppSettings["WebVersion"] %>'></script>

<style>
        .modalBackground {
         background-color:White;
         filter:alpha(opacity=70);
         opacity:0.7;
        }

        .modalPopup {
         background-color:#FFD9D5;
         border-width:3px;
         border-style:solid;
         border-color:Gray;
         padding:3px;
         width:250px;
        }
    </style>

        <!-- Buscador -->
        <div class="fila-ajustable" id="divSearchCustomer" runat="server">


            <uc1:wucCustomerSearchReturnRecord ID="wucCustomerSearchReturnRecord" runat="server" />

        </div>




        <div id="divSearchOrder" runat="server">

            <uc2:wucOrderSearchReturnRecord ID="wucOrderSearchReturnRecord" runat="server" />

        </div>


        <asp:HiddenField ID="hdCurrentID" runat="server" ClientIDMode="Static" Visible="False" />
        <asp:HiddenField ID="hdCurrentIndex" runat="server" ClientIDMode="Static" />



                    <table width="100%" border="0" align="left" cellpadding="5" cellspacing="0" >
                        <tr>
                        <td align="left" >

                        <asp:HyperLink ID="lnkEnlace_del_pdf" runat="server" ClientIDMode="Static" CssClass="boton_basico boton_imprimir" Text="Impresión Electrónica" Target="_blank"  style="margin-left:3px; ">
                        </asp:HyperLink>

                        <asp:LinkButton ID="btnPrint" runat="server" ClientIDMode="Static" CssClass="boton_basico boton_imprimir" Text="Imprimir" style="margin-left:3px; " TabIndex="40" OnClick="btnPrint_Click"/>

                        <asp:LinkButton ID="btnNewOrder" runat="server" CssClass="boton_basico boton_agregar" Text="Nuevo Pedido" style="margin-left:3px; " TabIndex="42" OnClick="btnNewOrder_Click" />

                        <asp:LinkButton ID="btnPosted" runat="server" CssClass="boton_basico boton_pagado" Text="Pagado" style="margin-left:3px; " TabIndex="43" OnClick="btnPosted_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnUnPosted" runat="server" CssClass="boton_basico boton_cerrar2" Text="Deshacer Pago" style="margin-left:3px; " TabIndex="44" OnClick="btnUnPosted_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnShipped" runat="server" CssClass="boton_basico boton_entregado" Text="Entregado" style="margin-left:3px; " TabIndex="45" OnClick="btnShipped_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnUnShipped" runat="server" CssClass="boton_basico boton_cerrar2" Text="Cancelar Entrega" style="margin-left:3px; " TabIndex="46" OnClick="btnUnShipped_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnSave" runat="server" CssClass="boton_basico boton_guardar" Text="Guardar" style="margin-left:3px; " TabIndex="47" OnClick="btnSave_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnEditOrder" runat="server" CssClass="boton_basico boton_editar" Text="Más Opciones" style="margin-left:3px; " TabIndex="48" OnClick="btnEditOrder_Click" />

                        <asp:LinkButton ID="btnSerialClean" runat="server" CssClass="boton_basico boton_guardar" Text="Limpiar Serie" style="margin-left:3px; " TabIndex="47" OnClick="btnSerialClean_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnCancelOrder" runat="server" CssClass="boton_basico boton_anular" Text="Anular Pedido" style="margin-left:3px; " TabIndex="47" OnClick="btnCancelOrder_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnGenerateElectronicDocument" runat="server" CssClass="boton_basico boton_agregar" Text="Generar Documento Electrónico" style="margin-left:3px; " TabIndex="47" OnClick="btnGenerateElectronicDocument_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnCancelElectronicDocument" runat="server" CssClass="boton_basico boton_anular" Text="Anular Documento Electrónico" style="margin-left:3px; " TabIndex="47" OnClick="btnCancelElectronicDocument_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnEmailElectronicDocument" runat="server" CssClass="boton_basico boton_sms" Text="Reenviar Email" style="margin-left:3px; " TabIndex="47" OnClick="btnEmailElectronicDocument_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnGenerateCreditNote" runat="server" CssClass="boton_basico boton_agregar" Text="Generar Nota de Crédito/Débito" style="margin-left:3px; " TabIndex="47" OnClick="btnGenerateCreditNote_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnViewCreditNote" runat="server" CssClass="boton_basico boton_editar" Text="Ver Nota de Crédito/Débito" style="margin-left:3px; " TabIndex="47" OnClick="btnViewCreditNote_Click" ValidationGroup="ValidateOrderSave" />

                        <asp:LinkButton ID="btnChangeWarehouse" runat="server" CssClass="boton_basico boton_entregado2" Text="Cambiar Almacén" style="margin-left:3px; " TabIndex="47" OnClick="btnChangeWarehouse_Click" ValidationGroup="ValidateOrderSave" />


                        </td>
                        </tr>

                        <tr>
                        <td align="right" >
                        <div style="border-bottom: 1px solid #e0e0e0; height: 1px; " >
                        </div>
                        </td>
                        </tr>
                    </table>


        <!-- Principal -->
        <div class="fila-ajustable" id="divPrincipal" runat="server">



            <!-- Paso 1 -->
            <div class="columna_ancho8" >
            <div class="color_de_bloque bloque_basico " >


            <div class="titulo_de_bloque2"><h4></h4></div>

                    <ul id="Ul1" class="menu menu_con_tabs" data-toggle="tabs" runat="server"  visible="false" >
                        <li id="Li1" runat="server" clientidmode="Static">
                        <a href="#contenido_tab1"><asp:Label ID="t1" runat="server" Text="Paso 1"></asp:Label></a>
                        </li>
                        <li id="Li2" runat="server" clientidmode="Static">
                        <a href="#contenido_tab2"><asp:Label ID="t2" runat="server" Text="Paso 2"></asp:Label></a>
                        </li>
                        <li id="Li3" runat="server" clientidmode="Static">
                        <a href="#contenido_tab3"><asp:Label ID="t3" runat="server" Text="Paso 3"></asp:Label></a>
                        </li>
                        <li >
                        <a href="#contenido_tab4"><asp:Label ID="t4" runat="server" Text="Paso 4"></asp:Label></a>
                        </li>
                        <li >
                        <a href="#contenido_tab5"><asp:Label ID="t5" runat="server" Text="Paso 5"></asp:Label></a>
                        </li>
                        <li>
                        <a href="#contenido_tab6"><asp:Label ID="t6" runat="server" Text="Paso 6"></asp:Label></a>
                        </li>
                        <li >
                        <a href="#contenido_tab7"><asp:Label ID="t7" runat="server" Text="Paso 7"></asp:Label></a>
                        </li>
                        <li>
                        <a href="#contenido_tab8"><asp:Label ID="t8" runat="server" Text="Paso 8"></asp:Label></a>
                        </li>
                    </ul>



                     <!-- Menu Tabs Acordeon / Izquierda-->

                    <div class="contenido_de_bloque" style="border-bottom: 1px solid #e0e0e0; min-height: 664px; " >


                    <table width="100%" border="0" align="right" cellpadding="5" cellspacing="0" style="margin-top:10px; ">
                        <tr>
                        <td align="left">
                        <span class="etiqueta_azul" style="margin-right:15px; ">
                            <asp:Label ID="lblEwalletAvailableCredits" runat="server" ClientIDMode="Static" Text="Créditos Ewallet: "></asp:Label>
                            <asp:Label ID="lbEwalletAvailableCredits" runat="server" ClientIDMode="Static"></asp:Label>
                        </span>

                        <span class="etiqueta_azul">
                        <asp:Label ID="lblExtraLifeAvailableCredits" runat="server" ClientIDMode="Static" Text="Créditos ExtraLife: "></asp:Label>
                        <asp:Label ID="lbExtraLifeAvailableCredits" runat="server" ClientIDMode="Static"></asp:Label>
                        </span>

                        <hr class="margen_hr">
                        
                        <asp:Label ID="Label34" runat="server" class="etiqueta_azul_2" ClientIDMode="Static" Text="1"></asp:Label>
                        <asp:Label ID="Label51" runat="server" class="texto_gris_estado" ClientIDMode="Static" Text="Ingresado"></asp:Label>
                        <asp:Label ID="lblLine1" runat="server" CssClass="texto_gris_estado" Text="&nbsp;&nbsp;/&nbsp;&nbsp;" ></asp:Label>
                        <asp:Label ID="Label48" runat="server" ClientIDMode="Static" class="etiqueta_azul_2" Text="2"></asp:Label>
                        <asp:Label ID="Label52" runat="server" class="texto_gris_estado" ClientIDMode="Static" Text="Pagado"></asp:Label>
                        <asp:Label ID="Label42" runat="server" CssClass="texto_gris_estado" Text="&nbsp;&nbsp;/&nbsp;&nbsp;" ></asp:Label>
                        <asp:Label ID="Label49" runat="server" ClientIDMode="Static" class="etiqueta_azul_2" Text="3"></asp:Label>
                        <asp:Label ID="Label53" runat="server" class="texto_gris_estado" ClientIDMode="Static" Text="Entregado"></asp:Label>
                        <asp:Label ID="Label47" runat="server" CssClass="texto_gris_estado" Text="&nbsp;&nbsp;/&nbsp;&nbsp;" ></asp:Label>
                        <asp:Label ID="Label50" runat="server" ClientIDMode="Static" class="etiqueta_azul_2" Text="0"></asp:Label>
                        <asp:Label ID="Label54" runat="server" class="texto_gris_estado" ClientIDMode="Static" Text="Anulado"></asp:Label>
                        &nbsp;
                        <span class="etiqueta_azul" >
                        <asp:Label ID="lblOrderStatus" runat="server" ClientIDMode="Static" Text="Estado"></asp:Label>
                        &nbsp;
                        <asp:Label ID="lbOrderStatus" runat="server" ClientIDMode="Static"></asp:Label>
                        </span>

                        <hr class="margen_hr">

                        <span class="etiqueta_azul" style="background-color:#8c8c8c !important; margin-right:15px; ">
                        <asp:Label ID="lblAceptada_por_sunat" runat="server" Text="Aceptada por Sunat: "></asp:Label>
                        <asp:Label ID="lbAceptada_por_sunat" runat="server"></asp:Label>
                        </span>
<%--                            <span class="etiqueta_azul" style="background-color:#8c8c8c !important; ">
                        <asp:HyperLink ID="lnkEnlace_del_pdf" runat="server" Text="Versión Digital" Target="_blank" style="color: white !important;">
                        </asp:HyperLink>
                        </span>--%>
                        <span class="etiqueta_azul" style="background-color:#8c8c8c !important; ">
                        <asp:Label ID="lblOrderID" runat="server" Text="Orden #"></asp:Label>
                        <asp:Label ID="lbOrderID" runat="server"></asp:Label>
                        </span>

                        <hr class="margen_hr">

                        </td>
                        </tr>
                    </table>

                    <br>
                    <table width="100%" border="0" align="right" cellpadding="5" cellspacing="0" style="margin-top:15px; display: none;">
                        <tr>
                        <td align="right" >
                        <asp:Label ID="Label55" runat="server" Text="Fecha:"></asp:Label>
                        <asp:Label ID="lbOrderDate" runat="server"></asp:Label>
                        </td>
                        </tr>
                    </table>
                    <hr><br>


                    <div class="tabs_lado_izquierda clearfix">

                            <ul class="menu menu_con_tabs tabs_izquierda_menu" data-toggle="tabs">
                                <li id="sup_contenido_tab1" runat="server" clientidmode="Static"><a href="#contenido_tab1" onclick="$('#hdCurrentIndex').val(1);">
                                <asp:Label ID="lblTabMenu1" runat="server" TabIndex="49" 
                                        Text="Productos" meta:resourcekey="lblVTabMenu1Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab2" runat="server" clientidmode="Static"><a href="#contenido_tab2" onclick="$('#hdCurrentIndex').val(2);">
                                <asp:Label ID="lblTabMenu2" runat="server" TabIndex="50" 
                                        Text="Pago"  meta:resourcekey="lblVTabMen2Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab3" runat="server" clientidmode="Static"><a href="#contenido_tab3" onclick="$('#hdCurrentIndex').val(3);">
                                <asp:Label ID="lblTabMenu3" runat="server" TabIndex="51" 
                                        Text="Dirección" meta:resourcekey="lblVTabMen3Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab4" runat="server" clientidmode="Static"><a href="#contenido_tab4" onclick="$('#hdCurrentIndex').val(4);">
                                <asp:Label ID="Label31" runat="server" TabIndex="52" 
                                        Text="Datos de Impresión" ></asp:Label></a></li>
                                <li id="sup_contenido_tab5" runat="server" clientidmode="Static"><a href="#contenido_tab5" onclick="$('#hdCurrentIndex').val(5);">
                                <asp:Label ID="Label3" runat="server" TabIndex="53" 
                                        Text="Rastreo" meta:resourcekey="lblVTabMen5Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab6" runat="server" clientidmode="Static"><a href="#contenido_tab6" onclick="$('#hdCurrentIndex').val(6);">
                                <asp:Label ID="Label4" runat="server" TabIndex="54" 
                                        Text="Notas" meta:resourcekey="lblVTabMen6Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab7" runat="server" clientidmode="Static"><a href="#contenido_tab7" onclick="$('#hdCurrentIndex').val(7);">
                                <asp:Label ID="lblTabMenu5" runat="server" TabIndex="55" 
                                        Text="Control Financiero" meta:resourcekey="lblVTabMen7Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab8" runat="server" clientidmode="Static"><a href="#contenido_tab8" onclick="$('#hdCurrentIndex').val(8);">
                                <asp:Label ID="lblTabMenu6" runat="server" TabIndex="56"
                                        Text="Control Administrativo" meta:resourcekey="lblVTabMen8Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab9" runat="server" clientidmode="Static"><a href="#contenido_tab9" onclick="$('#hdCurrentIndex').val(9);">
                                <asp:Label ID="Label2" runat="server" 
                                        Text="Mensaje de sistema" meta:resourcekey="lblVTabMen9Resource1" ></asp:Label></a></li>
                                <li id="sup_contenido_tab10" runat="server" clientidmode="Static"><a href="#contenido_tab10" onclick="$('#hdCurrentIndex').val(10);">
                                <asp:Label ID="lblTabMenu8" runat="server"  TabIndex="57"
                                        Text="Completado" meta:resourcekey="lblVTabMen10Resource1" ></asp:Label></a></li>
                            </ul>
                             <br> <br>
                    <!-- Contenido de Tabs -->

                    <div class="tabs_contenido" style="min-height: 565px; " >
                    <br>


                        <!-- Tab 1 Productos -->
                        <div class="tab_panel" id="contenido_tab1" runat="server" clientidmode="Static">


                            <asp:Panel id="div1Products" runat="server">

                            <table width="100%" border="0" align="center" cellpadding="6" cellspacing="0" style="margin-top:-10px;">
                            <tr>
                            <td align="right" >
                            <asp:Label ID="Label57" runat="server" Text="Seleccione el almacén" ></asp:Label>
                            </td>
                            <td align="right" width="45%">
                            <div data-tooltip="Seleccione el almacén" class="tooltip-bottom" >
                            <asp:DropDownList ID="ddlWarehouse" runat="server" onselectedindexchanged="ddlWarehouse_SelectedIndexChanged" AutoPostBack="true"
                            CssClass="campo_texto_select_almacen2" TabIndex="58" placeholder="Almacén">
                            </asp:DropDownList>
                            </div>
                            </td>
                            </tr>
                            </table>

<%--                            <hr>--%>

                            <table width="100%" border="0" align="center" cellpadding="6" cellspacing="0" >
                                <tr>
                                <td align="right">
                                <div data-tooltip="Buscar producto" class="tooltip-bottom" style="margin-top:-12px;">
                                <asp:TextBox ID="txtProductFilter" runat="server" ClientIDMode="Static" MaxLength="30" 
                                CssClass="campo_texto_busqueda_producto" placeholder="Buscar producto" TabIndex="59" ></asp:TextBox>
                                </div>
                                <%--</td>
                                <td align="right" width="45%">--%>

<%--                                <div data-tooltip="Filtrar productos" class="tooltip-bottom" >
                                <asp:DropDownList ID="DropDownList1" runat="server" CssClass="campo_texto_select_filtro" TabIndex="60" >
                                <asp:ListItem Text="Mostrar Todo" Value="1" ></asp:ListItem>
                                <asp:ListItem Text="Bebidas" Value="2" ></asp:ListItem>
                                <asp:ListItem Text="Promociones" Value="3" ></asp:ListItem>
                                <asp:ListItem Text="Paquetes" Value="4" ></asp:ListItem>
                                <asp:ListItem Text="Marketing" Value="5" ></asp:ListItem>
                                <asp:ListItem Text="Otros" Value="6" ></asp:ListItem>
                                </asp:DropDownList>
                                </div>--%>
                                </td>
                                </tr>
                            </table>

                            <hr>


                        <div style="height:680px; overflow-y: scroll; overflow-x: hidden;">
                        <asp:DataList ID="dtlProducts" runat="server" RepeatColumns="1"  ClientIDMode="Static" width="98%" RepeatDirection="Horizontal">
                            <ItemTemplate>
                            <asp:HiddenField ID="hdID" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "ID") %>' Visible="false" />
                            <div class="boton_clientes_lista" >
                            <table width="100%" border="0" align="center" cellpadding="6" cellspacing="0" >
                            <tr>

                            <td align="left" valign="top" width="14%">
                            <asp:Image ID="imgProduct" runat="server" ImageUrl='<%# "~/Styles/images/Products/"+DataBinder.Eval(Container.DataItem, "ProductID")+"_100.png" %>' style="margin-right: -10px; " 
                            CssClass="producto_foto_adaptable_lista"/>
                            </td>

                            <td align="left" valign="top" width="62%">
                            <h4><asp:Label ID="lbProductName" runat="server" Text='<%# DataBinder.Eval(Container.DataItem, "ProductName") %>' Font-Bold="true" ></asp:Label></h4>
                            <asp:Label ID="lbProductDescription" runat="server" Text='<%# DataBinder.Eval(Container.DataItem, "Description") %>' CssClass="texto_en_tablet" Visible="false"></asp:Label>
                            </td>

                            <td align="right" valign="top" width="24%">
                            <h4><asp:Label ID="lbProductPrice" runat="server" Text='<%# string.Format("$ {0:###,##0.00}", DataBinder.Eval(Container.DataItem, "WholesalePrice")) %>' ></asp:Label></h4>
                            <asp:ImageButton ID="btnProductAdd" runat="server" TabIndex="61"
                                    CssClass="boton_carrito colocar_derecha" 
                                    ImageUrl="~/Styles/2015/img/boton_carrito_espacio.png" 
                                    ValidationGroup="ValidateProductAdd" onclick="btnProductAdd_Click" />
                            </td>

                            </tr>
                            </table>
                            </div>

                            </ItemTemplate>
                        </asp:DataList>
                        </div>
                               </asp:Panel>
                        </div>

                        <!-- Tab 2 Pedido / Pago -->
                        <div class="tab_panel" id="contenido_tab2" runat="server" clientidmode="Static">
                        <asp:Panel id="div2Payment" runat="server">
                        
                            <h4><asp:Label ID="Label27" runat="server" Text="Tipo de envío"></asp:Label></h4>
                            <hr>
                            <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                                <tr>
                                <td align="right">
                                <asp:Label ID="Label25" runat="server" Text="Tipo de entrega" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Tipo de entrega">
                                <asp:DropDownList ID="ddlDeliveryTypeID" runat="server" 
                                onselectedindexchanged="ddlDeliveryTypeID_SelectedIndexChanged" AutoPostBack="true"
                                CssClass="campo_texto_select_pedidos2_xl" TabIndex="100" placeholder="Tipo de envío">
                                </asp:DropDownList>
                                </div>
                                </td>
                                </tr>

                                <tr>
                                <td align="right">
                                <asp:Label ID="Label24" runat="server" Text="Tipo de envío" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Tipo de envío">
                                <asp:DropDownList ID="ddlShipTypeID" runat="server" 
                                onselectedindexchanged="ddlShipTypeID_SelectedIndexChanged" AutoPostBack="true"
                                CssClass="campo_texto_select_pedidos2_xl" TabIndex="101" placeholder="Tipo de envío">
                                </asp:DropDownList>
                                </div>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label64" runat="server" Text="Tarifa" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Tarifa">
                                <asp:DropDownList ID="ddlShipMethodID" runat="server" 
                                onselectedindexchanged="ddlShipMethodID_SelectedIndexChanged" AutoPostBack="true"
                                CssClass="campo_texto_select_pedidos2_xl" TabIndex="102" placeholder="Tarifa">
                                </asp:DropDownList>
                                </div>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label65" runat="server" Text="Empresa Courier" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Empresa Courier">
                                <asp:DropDownList ID="ddlCarrierID" runat="server" ClientIDMode="Static" TabIndex="103"
                                    CssClass="campo_texto_select_pedidos2_xl" placeholder="Empresa Courier">
                                </asp:DropDownList>
                                </div>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label84" runat="server" Text="Flete" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Flete" >
                                <asp:TextBox ID="txtShipCost" runat="server" ClientIDMode="Static" CssClass="campo_texto_simple_3_xl" TabIndex="104" 
                                placeholder="Flete" MaxLength="20" ></asp:TextBox>
                                <asp:RequiredFieldValidator ID="rfvShipCost" runat="server" ControlToValidate="txtShipCost" ErrorMessage="*" Font-Bold="True" 
                                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateShipCost"></asp:RequiredFieldValidator>
                                <asp:CompareValidator ID="cvShipCost" runat="server" Text="*" ControlToValidate="txtShipCost" Display="Dynamic" 
                                    ErrorMessage="Error Amount" ForeColor="Red" Operator="DataTypeCheck" SetFocusOnError="True" Type="Double" ValidationGroup="ValidateShipCost"></asp:CompareValidator>
                                </div>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                </td>
                                <td align="left">
                                <asp:Button ID="btnUpdateShipCost" runat="server" CssClass="boton_basico etiqueta_naranja_grande" TabIndex="105"
                                    Text="Actualizar Flete" ValidationGroup="ValidateShipCost" clientidmode="Static" OnClick="btnUpdateShipCost_Click" />
                                </td>
                                </tr>
                                </table>


                            <br><br>
                            <h4><asp:Label ID="Label26" runat="server" Text="Documento de facturación"></asp:Label></h4>
                            <hr>
                            <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                                <tr>
                                <td align="right">
                                <asp:Label ID="Label85" runat="server" Text="Ticket / Boleta" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Ticket / Boleta">
                                <asp:DropDownList ID="ddlOrderDocument" runat="server" CssClass="campo_texto_select_pedidos2_xl" TabIndex="106"
                                    placeholder="Tipo de Documento" onselectedindexchanged="ddlOrderDocument_SelectedIndexChanged" AutoPostBack="true">
                                <asp:ListItem Text="Boleta" Value="1"></asp:ListItem>
                                <asp:ListItem Text="Factura" Value="2"></asp:ListItem>
                                    </asp:DropDownList>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label86" runat="server" Text="RUC / NIT" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="RUC / TAXID">
                                <asp:TextBox ID="txtTaxID" runat="server" CssClass="campo_texto_simple_3_xl" TabIndex="107"
                                        placeholder="RUC / NIT" MaxLength="20" ></asp:TextBox>
                                <asp:RequiredFieldValidator ID="rfvTaxID" runat="server" ControlToValidate="txtTaxID" ErrorMessage="*" Font-Bold="True" 
                                style="margin-right:-7px" ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateOrderDocument"></asp:RequiredFieldValidator>
                                <asp:RegularExpressionValidator ID="revTaxID" runat="server" ControlToValidate="txtTaxID" 
                                ErrorMessage="Ingrese un formato valido."
                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateOrderDocument"
                                Display="Dynamic" ValidationExpression="\d{4}[-]\d{6}[-]\d{3}[-]\d{1}|^\d{14}|^\d{11}|^\d{8}" ></asp:RegularExpressionValidator>

                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label87" runat="server" Text="Razón Social" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Compañia">
                                <asp:TextBox ID="txtCompany" runat="server" CssClass="campo_texto_simple_3_xl" TabIndex="108"
                                        placeholder="Compañia" MaxLength="45" ></asp:TextBox>
                                <asp:RequiredFieldValidator ID="rfvCompany" runat="server" ControlToValidate="txtCompany" ErrorMessage="*" Font-Bold="True" style="margin-right:-7px "
                                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateOrderDocument"></asp:RequiredFieldValidator>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label93" runat="server" Text="NRC" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="NCR">
                                <asp:TextBox ID="txtNRC" runat="server" CssClass="campo_texto_simple_3_xl" TabIndex="107"
                                        placeholder="Número de Registro de Contribuyente" MaxLength="20" ></asp:TextBox>
                                <asp:RequiredFieldValidator ID="rfvNRC" runat="server" ControlToValidate="txtNRC" ErrorMessage="*" Font-Bold="True" 
                                style="margin-right:-7px" ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateOrderDocument"></asp:RequiredFieldValidator>
                                <asp:RegularExpressionValidator ID="revNRC" runat="server" ControlToValidate="txtNRC" 
                                ErrorMessage="Ingrese un formato valido."
                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateOrderDocument"
                                Display="Dynamic" ValidationExpression="\d{6}[-]\d{1}|^\d{7}" ></asp:RegularExpressionValidator>

                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>

                            </table>



                            <br><br>
                            <div class="colocar_derecha" >
                            <table width="46%" border="0" align="right" cellpadding="2" cellspacing="0">
                                <tr>
                                <td><asp:Label ID="Label5" runat="server" CssClass="texto_gris_estado" Text="Aceptamos"></asp:Label></td>
                                <td align="left"><asp:Image ID="Image6" runat="server" ImageUrl="~/Styles/2015/img/tarjeta_american.gif"  /></td>
                                <td align="left"><asp:Image ID="Image7" runat="server" ImageUrl="~/Styles/2015/img/tarjeta_visa.gif"  /></td>
                                <td align="left"><asp:Image ID="Image2" runat="server" ImageUrl="~/Styles/2015/img/tarjeta_mastercard.gif"  /></td>
                                </tr>
                            </table>
                            </div><br>
                            <h4><asp:Label ID="Label38" runat="server" Text="Método de pago"></asp:Label></h4>


                            <hr>
                            <br>
                            <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                                <tr>
                                <td align="right">
                                <h4><b><asp:Label ID="lblIsSuscription" runat="server" Text="SUSCRIPCIÓN" ></asp:Label></b></h4>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Suscripción Mensual">
                                    <div class="ocultar_check" ><br />
<%--                                    <div data-tooltip="Es Suscripción" class="tooltip-top" >--%>
                                        <asp:CheckBox id="chkIsSuscription" runat="server" ClientIDMode="Static" TabIndex="88"/><label for="chkIsSuscription"></label>
<%--                                    </div>--%>
                                    </div>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label88" runat="server" Text="Metodo de pago" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Metodo de pago">
                                <asp:DropDownList ID="ddlPaymentType" runat="server" ClientIDMode="Static" CssClass="campo_texto_select_pedidos2_xl" 
                                TabIndex="109" placeholder="Metodo de pago">
                                </asp:DropDownList>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label89" runat="server" Text="Ingrese el monto" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Ingrese el monto">
                                <asp:TextBox ID="txtPaymentAmount" runat="server" ClientIDMode="Static" CssClass="campo_texto_escribir_xl" TabIndex="110" 
                                MaxLength="6" placeholder="Ingrese el monto"></asp:TextBox>
                                <asp:RequiredFieldValidator ID="rfvPaymentAmount" runat="server" ControlToValidate="txtPaymentAmount" ErrorMessage="*" Font-Bold="True" 
                                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidatePaymentAdd"></asp:RequiredFieldValidator>
                                <asp:CompareValidator ID="cvPaymentAmount" runat="server" Text="*" ControlToValidate="txtPaymentAmount" Display="Dynamic" 
                                    ErrorMessage="Error Amount" ForeColor="Red" Operator="DataTypeCheck" SetFocusOnError="True" Type="Double" ValidationGroup="ValidatePaymentAdd"></asp:CompareValidator>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label90" runat="server" Text="Fecha de Pago" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Fecha de Pago">
                                <asp:TextBox ID="txtPaymentDate" runat="server" ClientIDMode="Static"  CssClass="campo_texto_fecha_xl" TabIndex="111" 
                                MaxLength="10" placeholder="Fecha de Pago" ></asp:TextBox>
                                <asp:RequiredFieldValidator ID="rfvPaymentDate" runat="server" ControlToValidate="txtPaymentDate" Display="Dynamic"
                                    ErrorMessage="*" ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidatePaymentAdd"></asp:RequiredFieldValidator>
                                <asp:CompareValidator ID="cvPaymentDate" runat="server" Text="*" ControlToValidate="txtPaymentDate" Display="Dynamic" 
                                    ErrorMessage="Error Date" ForeColor="Red" Operator="DataTypeCheck" SetFocusOnError="True" Type="Date" ValidationGroup="ValidatePaymentAdd"></asp:CompareValidator>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                <asp:Label ID="Label91" runat="server" Text="Código de Autorización" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Código de Autorización">
                                <asp:TextBox ID="txtNumOper" runat="server" ClientIDMode="Static"  CssClass="campo_texto_codigo_xl" TabIndex="112" 
                                MaxLength="10" placeholder="Código de Autorización" ></asp:TextBox>
                                </div>
<%--                                </div>--%>
                                </td>
                                </tr>


                                <tr>
                                <td align="right">
                                
                                </td>
                                <td align="left">
                                <asp:Button ID="btnPaymentAdd" runat="server" CssClass="boton_basico etiqueta_naranja_grande" Text="Añadir Pago" ValidationGroup="ValidatePaymentAdd" 
                                TabIndex="113" clientidmode="Static" OnClick="btnPaymentAdd_Click" />
                                <br>
                                <asp:Label ID="Label37" runat="server" CssClass="etiqueta etiqueta_azul " meta:resourcekey="lbMessageResource1"></asp:Label>
                                </td>
                                </tr>
                            </table>





                        <div class="fila-ajustable">
 


                        <table width="100%" border="0" align="center" cellspacing="0" cellpadding="0" >
                                <tr>
                                <td align="center">
                                <hr>
                                <asp:GridView ID="gvPayment" runat="server" CellPadding="3" CellSpacing="2" TabIndex="114" 
                                        AutoGenerateColumns="False" CssClass="tabla tabla_con_sombreado_intercalado borde_de_tabla">
                                    <Columns>
                                        <asp:BoundField DataField="PaymentDate" HeaderText="Fecha" DataFormatString="{0:yyyy-MM-dd}" >
                                        <ItemStyle HorizontalAlign="Center" Width="140px" />
                                        </asp:BoundField>
                                        <asp:BoundField DataField="PaymentTypeName" HeaderText="Tipo de Pago" >
                                        <ItemStyle HorizontalAlign="Center" Width="150px" />
                                        </asp:BoundField>
                                        <asp:BoundField DataField="PaymentAmount" HeaderText="Importe" >
                                        <ItemStyle HorizontalAlign="Center" Width="100px" />
                                        </asp:BoundField>
                                        <asp:BoundField DataField="NumOper" HeaderText="Origen" >
                                        <ItemStyle HorizontalAlign="Center" Width="100px" />
                                        </asp:BoundField>

                                        <asp:TemplateField>
                                            <ItemTemplate>
                                                    <asp:HiddenField ID="hdID" Value='<%# Eval("ID") %>' ClientIDMode="Static" runat="server" Visible="false" />
                                                    <asp:Button ID="btnPaymentDelete" runat="server" CssClass="boton_basico boton_blanco" Text="Eliminar" onclick="btnPaymentDelete_Click" />
                                            </ItemTemplate>
                                            <ItemStyle HorizontalAlign="Center" />
                                        </asp:TemplateField>

                                    </Columns>

                                    <FooterStyle BackColor="#F39B00" ForeColor="White" Font-Bold="True" 
                                        HorizontalAlign="Center" />
                                    <HeaderStyle CssClass="gridview-header"/>
                                    <PagerStyle BackColor="#DDDDDD"  CssClass="paginacion" HorizontalAlign="Left" />
                                    <RowStyle CssClass="paginacion" VerticalAlign="Middle" />
                                    <SelectedRowStyle BackColor="#2CD671" Font-Bold="True" ForeColor="White" />
                                    <SortedAscendingCellStyle BackColor="#FFF1D4" />
                                    <SortedAscendingHeaderStyle BackColor="#B95C30" />
                                    <SortedDescendingCellStyle BackColor="#F1E5CE" />
                                    <SortedDescendingHeaderStyle BackColor="#93451F" />


                                </asp:GridView>
                                </td>
                                </tr>
                        </table>

                        <br>
                        </div>

                        

                        </asp:Panel>
                        </div>


                        <!-- Tab 3 Dirección -->
                        <div class="tab_panel" id="contenido_tab3" runat="server" clientidmode="Static">
                        <asp:Panel id="div3Address" runat="server">

                        <h4><asp:Label ID="Label18" runat="server" Text="Dirección de envío / facturación"></asp:Label></h4>
                        <hr>

                        <table width="100%" border="0" align="center" cellspacing="0" cellpadding="1">
                        <tr>
                        <td align="right" >
                        <div class="controles-grupales tooltip-top" data-tooltip="Nombre">
                        <asp:TextBox ID="txtShippingName" runat="server" CssClass="campo_texto_persona_xl"
                            placeholder="Nombre" MaxLength="50" TabIndex="120"></asp:TextBox>
                        </div>
                        
                        
                        <div class="controles-grupales tooltip-top" data-tooltip="SSN/DNI">
                        <asp:TextBox ID="txtSSN" runat="server" CssClass="campo_texto_dni_xl" TabIndex="122" 
                            placeholder="SSN/DNI" MaxLength="20" ></asp:TextBox>
                        </div>

                        <div class="controles-grupales tooltip-top" data-tooltip="Teléfono">
                        <asp:TextBox ID="txtShippingPhone" runat="server" CssClass="campo_texto_movil_xl" TabIndex="123" 
                            placeholder="Teléfono" MaxLength="20" ></asp:TextBox>
                        </div>
                        
                        <div class="controles-grupales tooltip-top" data-tooltip="Dirección">
                        <%--<asp:Label ID="Label22" runat="server" CssClass="textored" Font-Bold="True" ForeColor="#DB352B" meta:resourcekey="Label6Resource1" Text="(*)&nbsp;"></asp:Label>
                        <asp:RequiredFieldValidator ID="rfvShippingline1" runat="server" ControlToValidate="txtShippingline1" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateShipping" EnableClientScript="false"></asp:RequiredFieldValidator>--%>
                        <asp:TextBox ID="txtShippingline1" runat="server" CssClass="campo_texto_ubicacion_xl" TabIndex="124" 
                            placeholder="Dirección" MaxLength="50" ></asp:TextBox>
                        </div>
                        
                        <div class="controles-grupales tooltip-top" data-tooltip="Dirección adicional">
                        <asp:TextBox ID="txtShippingline2" runat="server" CssClass="campo_texto_ubicacion_xl"
                            placeholder="Dirección adicional" MaxLength="50"  TabIndex="125" ></asp:TextBox>
                        </div>

                        
                        <div class="controles-grupales tooltip-top" data-tooltip="Ciudad">
                        <%-- <asp:Label ID="Label19" runat="server" CssClass="textored" Font-Bold="True" ForeColor="#DB352B" meta:resourcekey="Label8Resource1" Text="(*)&nbsp;"></asp:Label>
                       <asp:RequiredFieldValidator ID="rfvShippingCity" runat="server" ControlToValidate="txtShippingCity" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateShipping" EnableClientScript="false"></asp:RequiredFieldValidator>--%>
                        <asp:TextBox ID="txtShippingCity" runat="server" CssClass="campo_texto_estado_xl" TabIndex="121" 
                        placeholder="Ciudad" MaxLength="20" ></asp:TextBox>
                        </div>

                        
                        <div class="controles-grupales tooltip-top" data-tooltip="Estado" style="display: none">
                        <%--<asp:Label ID="Label20" runat="server" CssClass="textored" Font-Bold="True"  ForeColor="#DB352B" Text="(*)&nbsp;"></asp:Label>
                        <asp:RequiredFieldValidator ID="rfvShippingState" runat="server" ControlToValidate="txtShippingState" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateShipping" EnableClientScript="false"></asp:RequiredFieldValidator>--%>
                        <asp:TextBox ID="txtShippingState" runat="server" CssClass="campo_texto_estado_xl"  TabIndex="126" 
                            placeholder="Estado" MaxLength="15" ></asp:TextBox>
                        </div>
                        
                        <div class="controles-grupales tooltip-top" data-tooltip="Código Postal" style="display: none">
                        <%--<asp:Label ID="Label21" runat="server" CssClass="textored" Font-Bold="True" ForeColor="#DB352B" meta:resourcekey="Label10Resource1" Text="(*)&nbsp;"></asp:Label>
                        <asp:RequiredFieldValidator ID="rfvShippingPostalCode" runat="server" ControlToValidate="txtShippingPostalCode" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateShipping" EnableClientScript="false"></asp:RequiredFieldValidator>--%>
                        <asp:TextBox ID="txtShippingPostalCode" runat="server" CssClass="campo_texto_codigo_xl"  TabIndex="127" 
                            placeholder="Código Postal" MaxLength="10" ></asp:TextBox>
                        </div>
                        
                        <div class="controles-grupales tooltip-top" data-tooltip="País">
                      <%--  <asp:Label ID="Label24" runat="server" CssClass="textored" Font-Bold="True"  ForeColor="#DB352B" meta:resourcekey="Label11Resource1" Text="(*)&nbsp;"></asp:Label>--%>
                        <asp:DropDownList ID="ddlShippingCountry" runat="server" Enabled="False" CssClass="campo_texto_select_pais_xl" TabIndex="128" 
                        placeholder="País" title="País"></asp:DropDownList>
                        </div>

                        <div class="controles-grupales tooltip-top" data-tooltip="Correo Electrónico">
                       <%--  <asp:Label ID="Label25" runat="server" CssClass="textored" Font-Bold="True" ForeColor="#DB352B" Text="(*)&nbsp;" meta:resourcekey="Label1Resource1"></asp:Label>
                       <asp:RequiredFieldValidator ID="rfvEmail" runat="server" ControlToValidate="txtEmail" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateShipping" EnableClientScript="false"></asp:RequiredFieldValidator>--%>
                        <asp:TextBox ID="txtEmail" runat="server" CssClass="campo_texto_email_xl" TabIndex="129" 
                            placeholder="Correo Electrónico" title="Correo Electrónico" MaxLength="30" ></asp:TextBox>
                        <asp:RegularExpressionValidator ID="revEmail" runat="server" ControlToValidate="txtEmail" ErrorMessage="*" ForeColor="Red" SetFocusOnError="True" Display="Dynamic"
                            ValidationExpression="\w+([-+.']\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*" ValidationGroup="ValidateShipping" EnableClientScript="false"></asp:RegularExpressionValidator>
                        </div>

                        <br>

                       <%-- <asp:Label ID="lblRequired" runat="server" CssClass="texto_normal" Font-Bold="True" ForeColor="#ff0000" meta:resourcekey="lblRequiredResource1" 
                        Text="(*) Información obligatoria"></asp:Label>--%>


                        <br><br>

                        </td>

                        <td align="right" width="20%" ></td>

                      </tr>
                   </table >


                            </asp:Panel>
                        </div>


                        <!-- Tab 4 Impresión -->
                        <div class="tab_panel" id="contenido_tab4" runat="server" clientidmode="Static">
                            <asp:Panel id="div4Printer" runat="server">
                            <h4><asp:Label ID="Label56" runat="server" Text="Datos de Impresión"></asp:Label></h4>
                            <hr>


                            <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                                <tr>
                                <td align="right">
                                <asp:Label ID="Label60" runat="server" Text="Impresora de Tickets" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Impresora de Tickets">
                                <asp:DropDownList ID="ddlPrintClientHostName" runat="server" CssClass="campo_texto_select_pedidos2_xl" TabIndex="140" 
                                onselectedindexchanged="ddlPrintClientHostName_SelectedIndexChanged" AutoPostBack="true"
                                data-placement="right" data-toggle="tooltip" placeholder="Cambiar Impresora de Tickets" title="Cambiar Impresora de Tickets" >
                                </asp:DropDownList>
                                </div>
                                </td>
                                </tr>

                                <tr>
                                <td align="right">
                                <asp:Label ID="Label61" runat="server" Text="Serie Máquina" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Serie Máquina">
                                <asp:TextBox ID="txtSerialPrinter" runat="server"  TabIndex="141" CssClass="campo_texto_simple_3_xl"
                                        placeholder="Serie Máquina" MaxLength="50" Enabled="false"></asp:TextBox>
                                </div>
                                </td>
                                </tr>

                                <tr>
                                <td align="right" width="40%">
                                    <asp:Label ID="Label58" runat="server" Text="Número de Serie"></asp:Label>
                                </td>
                                <td align="left" width="60%">
                                <div class="controles-grupales tooltip-top" data-tooltip="Número de Serie">
                                <asp:TextBox ID="txtSerialDocument" runat="server"  CssClass="campo_texto_simple_3_xl" 
                                        MaxLength="50" placeholder="Número de Serie" TabIndex="142" Enabled="false"></asp:TextBox>
                                </div>
                                </td>
                                </tr>

                                <tr>
                                <td align="right">
                                <asp:Label ID="Label59" runat="server" Text="Número de Documento" ></asp:Label>
                                </td>
                                <td align="left">
                                <div class="controles-grupales tooltip-top" data-tooltip="Número de Documento">
                                <asp:TextBox ID="txtSerialNumber" runat="server" TabIndex="143" CssClass="campo_texto_simple_3_xl"
                                        placeholder="Número de Documento" MaxLength="50" Enabled="false"></asp:TextBox>
                                </div>
                                </td>
                                </tr>

                                </table>

                            </asp:Panel>
                        </div>


                        <!-- Tab 5 Rastreo -->
                        <div class="tab_panel" id="contenido_tab5" runat="server" clientidmode="Static">
                            <asp:Panel id="div5Tracking" runat="server">
                            <h4><asp:Label ID="Label8" runat="server" Text="Rastreo"></asp:Label></h4>
                            <hr>
                        <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                        <tr>
                        <td align="right" width="40%">
                        <asp:Label ID="Label44" runat="server" Text="Track Code #" ></asp:Label>
                        </td>
                        <td align="left" width="60%">
                        <div class="controles-grupales tooltip-top" data-tooltip="Track Code">
                        <asp:TextBox ID="txtTrackCodeNumber" runat="server" CssClass="campo_texto_simple_3_xl" TabIndex="150" 
                                placeholder="Track Code" MaxLength="50" ></asp:TextBox> 
                        </div> 
                        <asp:RequiredFieldValidator ID="rfvTrackCodeNumber" runat="server" ControlToValidate="txtTrackCodeNumber" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateTrackingAdd" EnableClientScript="false"></asp:RequiredFieldValidator>
                        </td>
                        </tr>

                        <tr>
                        <td align="right" >
                        <asp:Label ID="Label41" runat="server" Text="Tipo de documento" ></asp:Label>
                        </td>
                        <td align="left" >
                        <div class="controles-grupales tooltip-top" data-tooltip="Tipo de documento">
                        <asp:DropDownList ID="ddlTrackingOrderDocument" runat="server" ClientIDMode="Static" 
                        CssClass="campo_texto_select_pedidos2_xl" TabIndex="151" >
                            <asp:ListItem Text="Ticket" Value="1"></asp:ListItem>
                            <asp:ListItem Text="Invoice" Value="2"></asp:ListItem>
                       <%--     <asp:ListItem Text="3" Value="3"></asp:ListItem>
                            <asp:ListItem Text="4" Value="4"></asp:ListItem>--%>
                        </asp:DropDownList>
                        </div>
                        </td>
                        </tr>

                        <tr>
                        <td align="right">
                        <asp:Label ID="Label45" runat="server" Text="Número de Documento" ></asp:Label>
                        </td>
                        <td align="left">
                        <div class="controles-grupales tooltip-top" data-tooltip="Número de Documento">
                        <asp:TextBox ID="txtOrderDocumentNumber" runat="server" CssClass="campo_texto_simple_3_xl" TabIndex="152" 
                                placeholder="Número de Documento" MaxLength="50" ></asp:TextBox>
                        </div>
                        <asp:RequiredFieldValidator ID="rfvOrderDocumentNumber" runat="server" ControlToValidate="txtOrderDocumentNumber" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateTrackingAdd"></asp:RequiredFieldValidator>
                        </td>
                        </tr>

                        <tr>
                        <td align="right">
                        <asp:Label ID="Label46" runat="server" Text="Fecha de envío" ></asp:Label>
                        </td>
                        <td align="left">
                        <div class="controles-grupales tooltip-top" data-tooltip="Fecha de envío">
                        <asp:TextBox ID="txtTrackDate" runat="server" ClientIDMode="Static" CssClass="campo_texto_simple_3_xl" TabIndex="153" 
                                placeholder="Fecha de envío" MaxLength="10" ></asp:TextBox>
                        </div>
                        <asp:RequiredFieldValidator ID="rfvTrackDate" runat="server" ControlToValidate="txtTrackDate" ErrorMessage="*" Font-Bold="True" 
                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateTrackingAdd"></asp:RequiredFieldValidator>
                        <asp:CompareValidator ID="cvTrackDate" runat="server" Text="*" ControlToValidate="txtTrackDate" Display="Dynamic" 
                            ErrorMessage="Error Date" ForeColor="Red" Operator="DataTypeCheck" SetFocusOnError="True" Type="Date" ValidationGroup="ValidateTrackingAdd"></asp:CompareValidator>
                        </td>
                        </tr>


                        </table>

                            </asp:Panel>
                        </div>


                        <!-- Tab 6 Notas -->
                        <div class="tab_panel" id="contenido_tab6" runat="server" clientidmode="Static">
                            <asp:Panel id="div6Notes" runat="server">
                            <h4><asp:Label ID="Label7" runat="server" Text="Notas"></asp:Label></h4>
                            <hr>
                            <table width="100%" border="0" align="center" cellspacing="0" cellpadding="4" >
                            <tr>
                                <%--<td align="right" width="40%" valign="top">
                                <div style="margin-top:10px !important;">
                                <asp:Label ID="Label23" runat="server" Text="Notas" ></asp:Label>
                                </div>
                                </td>--%>
                                <td align="left" width="60%">
                                <div class="controles-grupales tooltip-top" data-tooltip="Notas">
                                    <asp:TextBox ID="txtNotes" runat="server" data-placement="right" data-toggle="tooltip" 
                                     class="campo_texto_multilinea" 
                                    TabIndex="39" placeholder="" MaxLength="50" TextMode="MultiLine"></asp:TextBox>
                                </div>
                                </td>
                            </tr>
                            </table>

                            </asp:Panel>
                        </div>


                        <!-- Tab 7 Control Financiero -->
                        <div class="tab_panel" id="contenido_tab7" runat="server" clientidmode="Static">
                        <asp:Panel id="div7Accounting" runat="server">


                        <div class="colocar_derecha" style="margin-top:-15px !important;">
                        <asp:LinkButton ID="btnSaveAccounting" runat="server" CssClass="boton_basico boton_guardar colocar_derecha" Text="Guardar Cambios"  OnClick="btnSaveAccounting_Click" ValidationGroup="ValidateSaveOrderAccounting" />
                        </div>

                        <!-- Mas opciones / abrir -->
                                    <div id="tab1" class="tab_panel active">
                                        <div id="seccion1" class="acordeon" style="margin-bottom:0px !important; margin-top:15px;">
                                            <div class="acordeon_contenido">

                                                <a class="acordeon_desplegable" data-toggle="collapse" data-parent="#seccion1" href="#seccion1_1" 
                                                TabIndex="160" >
                                                <asp:ImageButton ID="ImageButton2" runat="server" CssClass="icono_adaptable_add" 
                                                ImageUrl="~/Styles/2015/img/boton_abrir.png"/>&nbsp;&nbsp;
                                                <asp:Label ID="Label43" runat="server" Text="Comprobante de Pago"></asp:Label>
                                                </a>

                                                <hr style="margin-top:7px !important; margin-bottom:7px !important;">
                                                <!-- Contenido 1 -->
                                                <div id="seccion1_1" class="collapse in" style="width:100%;">
                                                <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                                                <tr>
                                                <td align="right" width="40%">
                                                <asp:Label ID="Label10" runat="server" Text="Tipo de Comprobante de Pago" ></asp:Label>
                                                </td>
                                                <td align="left" width="60%">
                                                <div class="controles-grupales tooltip-bottom" data-tooltip="Tipo de Comprobante de Pago">
                                                <asp:DropDownList ID="ddlPaymentVoucherTypeID" runat="server" TabIndex="161" 
                                                        ClientIDMode="Static" CssClass="campo_texto_select_pedidos2_xl" 
                                                        placeholder="Tipo de Comprobante de Pago o Documento" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label13" runat="server" Text="Código de Equipo" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Código de Equipo">
                                                <asp:DropDownList ID="ddlPrintClientHostName2" runat="server" ClientIDMode="Static" 
                                                CssClass="campo_texto_select_pedidos2_xl" TabIndex="162" 
                                                placeholder="Código de Equipo">
                                                </asp:DropDownList>
                                                </div>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label11" runat="server" Text="Número de Serie" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Número de Serie">
                                                <asp:TextBox ID="txtSerialDocument2" runat="server" TabIndex="163" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Número de Serie" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label14" runat="server" Text="Serie Máquina" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Serie Máquina">
                                                <asp:TextBox ID="txtSerialPrinter2" runat="server" TabIndex="164" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Serie Máquina" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label12" runat="server" Text="Número de Documento" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Número de Documento">
                                                <asp:TextBox ID="txtSerialNumber2" runat="server" TabIndex="165" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Número de Documento" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label15" runat="server" Text="Número de Pedido" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Número de Pedido">
                                                <asp:TextBox ID="txtAccountingOrderID" runat="server" TabIndex="166" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Número de Pedido" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvAccountingOrderID" runat="server" ControlToValidate="txtAccountingOrderID" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label16" runat="server" Text="Asiento" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Asiento">
                                                <asp:TextBox ID="txtAccountingSeat" runat="server" TabIndex="167" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Asiento" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvAccountingSeat" runat="server" ControlToValidate="txtAccountingSeat" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>
                                                </table>
                                                <hr >
                                                </div>



                                                <a class="acordeon_desplegable" data-toggle="collapse" data-parent="#seccion1" href="#seccion1_2" 
                                                TabIndex="168">
                                                <asp:ImageButton ID="ImageButton1" runat="server" CssClass="icono_adaptable_add" 
                                                ImageUrl="~/Styles/2015/img/boton_abrir.png" />&nbsp;&nbsp;
                                                <asp:Label ID="Label36" runat="server" Text="Información del Cliente"></asp:Label>
                                                </a>
                                                
                                                <hr style="margin-top:7px !important; margin-bottom:7px !important;">
                                                <!-- Contenido 2 -->    
                                                <div id="seccion1_2" class="collapse" style="width:100%;">
                                                <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                        
                                                <tr>
                                                <td align="right" width="40%">
                                                <asp:Label ID="Label9" runat="server" Text="Tipo de Documento de Identidad" ></asp:Label>
                                                </td>
                                                <td align="left" width="60%">
                                                <div class="controles-grupales tooltip-bottom" data-tooltip="Tipo de Documento de Identidad">
                                                <asp:DropDownList ID="ddlIdentityDocumentID" runat="server" CssClass="campo_texto_select_pedidos2_xl" 
                                                TabIndex="169" placeholder="Tipo de Documento de Identidad">
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label17" runat="server" Text="Número" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Número">
                                                <asp:TextBox ID="txtDocumentNumber" runat="server" TabIndex="170" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Número" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvDocumentNumber" runat="server" ControlToValidate="txtDocumentNumber" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label30" runat="server" Text="Razón Social" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Razón Social">
                                                <asp:TextBox ID="txtCompanyName" runat="server" TabIndex="171" CssClass="campo_texto_simple_3_xl"
                                                        placeholder="Razón Social" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvCompanyName" runat="server" ControlToValidate="txtCompanyName" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                </table>
                                                <hr>
                                                </div>



                                                <a class="acordeon_desplegable" data-toggle="collapse" data-parent="#seccion1" href="#seccion1_3" 
                                                TabIndex="172">
                                                <asp:ImageButton ID="ImageButton3" runat="server" CssClass="icono_adaptable_add" 
                                                ImageUrl="~/Styles/2015/img/boton_abrir.png" />&nbsp;&nbsp;
                                                <asp:Label ID="Label66" runat="server" Text="Resumen Contable"></asp:Label>
                                                </a>

                                                <hr style="margin-top:7px !important; margin-bottom:7px !important;">
                                                <!-- Contenido 3 -->    
                                                <div id="seccion1_3" class="collapse" style="width:100%;">
                                                <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                        
                                                <tr>
                                                <td align="right" width="40%">
                                                <asp:Label ID="Label67" runat="server" Text="Moneda" ></asp:Label>
                                                </td>
                                                <td align="left" width="60%">
                                                <div class="controles-grupales tooltip-bottom" data-tooltip="Moneda">
                                                <asp:DropDownList ID="ddlCurrencyID" runat="server" CssClass="campo_texto_select_pedidos2_xl" TabIndex="173"
                                                        placeholder="Moneda" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label68" runat="server" Text="Base Imponible" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Base Imponible">
                                                <asp:TextBox ID="txtTaxableAmount" runat="server" TabIndex="174"
                                                        CssClass="campo_texto_simple_3_xl" placeholder="Base Imponible" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvTaxableAmount" runat="server" ControlToValidate="txtTaxableAmount" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label69" runat="server" Text="IGV/IVA" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="IGV/IVA">
                                                <asp:TextBox ID="txtTaxAmt" runat="server" TabIndex="175"
                                                        CssClass="campo_texto_simple_3_xl" placeholder="IGV/IVA" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvTaxAmt" runat="server" ControlToValidate="txtTaxAmt" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label70" runat="server" Text="Importe Total MN" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Importe Total MN">
                                                <asp:TextBox ID="txtTotalLocalCurrency" runat="server" TabIndex="176"
                                                        CssClass="campo_texto_simple_3_xl" placeholder="Importe Total MN" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvTotalLocalCurrency" runat="server" ControlToValidate="txtTotalLocalCurrency" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label71" runat="server" Text="Tipo de Cambio" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Tipo de Cambio">
                                                <asp:TextBox ID="txtExchangeRate" runat="server" TabIndex="177"
                                                        CssClass="campo_texto_simple_3_xl" placeholder="Tipo de Cambio" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvExchangeRate" runat="server" ControlToValidate="txtExchangeRate" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label72" runat="server" Text="Importe Total ME" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Importe Total ME">
                                                <asp:TextBox ID="txtTotalForeignCurrency" runat="server" TabIndex="178"
                                                        CssClass="campo_texto_simple_3_xl" placeholder="Importe Total ME" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvTotalForeignCurrency" runat="server" ControlToValidate="txtTotalForeignCurrency" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label73" runat="server" Text="Nota de Crédito" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Nota de Crédito">
                                                <asp:TextBox ID="txtCreditNoteNumber" runat="server" TabIndex="179"
                                                        CssClass="campo_texto_simple_3_xl" placeholder="Nota de Crédito" MaxLength="50" ></asp:TextBox>
                                                </div>
                                                <asp:RequiredFieldValidator ID="rfvCreditNoteNumber" runat="server" ControlToValidate="txtCreditNoteNumber" ErrorMessage="*" Font-Bold="True" 
                                                ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSaveOrderAccounting"></asp:RequiredFieldValidator>
                                                </td>
                                                </tr>

                                                </table>
                                                <hr>
                                                </div>




                                                <a class="acordeon_desplegable" data-toggle="collapse" data-parent="#seccion1" href="#seccion1_4" 
                                                TabIndex="180">
                                                <asp:ImageButton ID="ImageButton4" runat="server" CssClass="icono_adaptable_add" ImageUrl="~/Styles/2015/img/boton_abrir.png"/>&nbsp;&nbsp;
                                                <asp:Label ID="Label74" runat="server" Text="Otros"></asp:Label>
                                                </a>
                                                <hr style="margin-top:7px !important; margin-bottom:7px !important;">
                                                <!-- Contenido 4 -->    
                                                <div id="seccion1_4" class="collapse" style="width:100%;">
                                                <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0">
                        
                                                <tr>
                                                <td align="right" width="40%">
                                                <asp:Label ID="Label75" runat="server" Text="Medio de Pago" ></asp:Label>
                                                </td>
                                                <td align="left" width="60%">
                                                <div class="controles-grupales tooltip-bottom" data-tooltip="Medio de Pago">
                                                <asp:DropDownList ID="ddlPaymentMethodID" runat="server" CssClass="campo_texto_select_pedidos_xl" TabIndex="181"
                                                        placeholder="Medio de Pago" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label76" runat="server" Text="Tipo de Operación" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Tipo de Operación">
                                                <asp:DropDownList ID="ddlOperationTypeID" runat="server" CssClass="campo_texto_select_pedidos_xl" TabIndex="182"
                                                        placeholder="Tipo de Operación" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label77" runat="server" Text="Entidad Financiera" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Entidad Financiera">
                                                <asp:DropDownList ID="ddlBanksID" runat="server" CssClass="campo_texto_select_pedidos_xl" TabIndex="183"
                                                        placeholder="Entidad Financiera" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label78" runat="server" Text="Tipo de Existencia" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Tipo de Existencia">
                                                <asp:DropDownList ID="ddlStockTypeID" runat="server" CssClass="campo_texto_select_pedidos_xl" TabIndex="184"
                                                        placeholder="Tipo de Existencia" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label79" runat="server" Text="Unidad de Medida" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Unidad de Medida">
                                                <asp:DropDownList ID="ddlMeasurementUnitsID" runat="server" CssClass="campo_texto_select_pedidos_xl" 
                                                TabIndex="185" placeholder="Unidad de Medida" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label82" runat="server" Text="Tipo de Intangible" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Tipo de Intangible">
                                                <asp:DropDownList ID="ddlIntangibleAssetsTypeID" runat="server" CssClass="campo_texto_select_pedidos_xl" 
                                                TabIndex="186" placeholder="Tipo de Intangible" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label80" runat="server" Text="Código de Libro o Registro" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Código de Libro o Registro">
                                                <asp:DropDownList ID="ddlAccountingLedgerCodeID" runat="server" CssClass="campo_texto_select_pedidos_xl" 
                                                TabIndex="187" placeholder="Código de Libro o Registro" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label81" runat="server" Text="Cuenta Contable" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Cuenta Contable">
                                                <asp:DropDownList ID="ddlAccountingCodeID" runat="server" CssClass="campo_texto_select_pedidos_xl" 
                                                TabIndex="188" placeholder="Cuenta Contable" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>


                                                <tr>
                                                <td align="right">
                                                <asp:Label ID="Label83" runat="server" Text="Código de la Aduana" ></asp:Label>
                                                </td>
                                                <td align="left">
                                                <div class="controles-grupales tooltip-top" data-tooltip="Código de la Aduana">
                                                <asp:DropDownList ID="ddlCustomsCodeID" runat="server" CssClass="campo_texto_select_pedidos_xl" TabIndex="189"
                                                placeholder="Código de la Aduana" >
                                                </asp:DropDownList>
                                                </div>

                                                </td>
                                                </tr>
                                                </table>
                                                <br><br>
                                                </div>

                                            </div>

                                        </div>
                                    </div>





                        <br>
                            </asp:Panel>
                        </div>


                        <!-- Tab 8 Control Administrativo -->
                        <div class="tab_panel" id="contenido_tab8" runat="server" clientidmode="Static">
                            <asp:Panel id="div8AdministrativeControl" runat="server">

                            <h4><asp:Label ID="Label6" runat="server" Text="Control Administrativo"></asp:Label></h4>
                            
                            <hr>

                            <table width="100%" border="0" align="center" cellspacing="0" cellpadding="5" >
                            <tr>
                                <td align="center" >
                                <asp:DropDownList ID="DropDownList8" runat="server" ClientIDMode="Static" CssClass="campo_texto_select_pedidos_xl" 
                                TabIndex="200" placeholder="Metodo de pago" Visible="False">
                                        <asp:ListItem Text="Editar Pedido (UnPosted)" Value="1"></asp:ListItem>
                                        <asp:ListItem Text="Anular Entrega (UnShipped)" Value="2"></asp:ListItem>
                                        <asp:ListItem Text="Devolución de Mercadería (RMA)" Value="3"></asp:ListItem>
                                        <asp:ListItem Text="Eliminar Pedido (Deleted)" Value="4"></asp:ListItem>
                                </asp:DropDownList>
                                </td>
                                <td align="right" >
                                </td>
                            </tr>

                            <tr>
                                <td align="right" width="40%">
                                <asp:Label ID="Label35" runat="server" Text="Fecha del Pedido"></asp:Label>
                                </td>
                                <td align="left" width="60%">
                                <div class="controles-grupales tooltip-top" data-tooltip="Fecha del Pedido">
                                <asp:TextBox ID="txtOrderDate" runat="server" ClientIDMode="Static"  CssClass="campo_texto_fecha_xl" TabIndex="201" MaxLength="10" 
                                    placeholder="Fecha del Pedido" ></asp:TextBox>
                                </div>
                                <asp:RequiredFieldValidator ID="rfvOrderDate" runat="server" ControlToValidate="txtOrderDate" ErrorMessage="*" Font-Bold="True" 
                                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateAdministrativeControl"></asp:RequiredFieldValidator>
                                <asp:CompareValidator ID="cvOrderDate" runat="server" Text="*" ControlToValidate="txtOrderDate" Display="Dynamic" 
                                    ErrorMessage="Error Date" ForeColor="Red" Operator="DataTypeCheck" SetFocusOnError="True" Type="Date" ValidationGroup="ValidateAdministrativeControl"></asp:CompareValidator>
                                </td>
                            </tr>

                                <tr>
                                    <td align="right" width="36%">
                                    <asp:Label ID="Label40" runat="server" Text="Fecha del Bono"></asp:Label>
                                    </td>
                                    <td align="left">
                                    <div class="controles-grupales tooltip-top" data-tooltip="Fecha del Bono">
                                    <asp:TextBox ID="txtBonusDate" runat="server" ClientIDMode="Static" 
                                            CssClass="campo_texto_fecha_xl" MaxLength="10" placeholder="Fecha del Bono" TabIndex="202" ></asp:TextBox>
                                    </div>

                                        <asp:RequiredFieldValidator ID="rfvBonusDate" runat="server" 
                                            ControlToValidate="txtBonusDate" ErrorMessage="*" Font-Bold="True" 
                                            ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateAdministrativeControl"></asp:RequiredFieldValidator>
                                        <asp:CompareValidator ID="cvBonusDate" runat="server" 
                                            ControlToValidate="txtBonusDate" Display="Dynamic" ErrorMessage="Error Date" 
                                            ForeColor="Red" Operator="DataTypeCheck" SetFocusOnError="True" Text="*" 
                                            Type="Date" ValidationGroup="ValidateAdministrativeControl"></asp:CompareValidator>
                                    </td>
                                </tr>

                                <tr>
                                    <td align="center">
                                        
                                    </td>
                                </tr>
                                <tr>
                                    <td align="center">

                                    </td>
                                </tr>
                                <tr>
                                    <td align="center">

                                    </td>
                                </tr>
                                <tr>
                                    <td align="center">

                                    </td>
                                </tr>
                                <tr>
                                    <td align="center">
                                    </td>
                                </tr>
    
                            </table>
                            <br>
                            </asp:Panel>
                        </div>


                        <!-- Tab 9 Mensaje de sistema -->
                        <div class="tab_panel" id="contenido_tab9" runat="server" clientidmode="Static">
                            <div class="texto_centrado">    
                        <!-- Error -->
                        <asp:Panel class="columna_ancho8" id="div9Error" runat="server">
                        <div class="bloque_basico color_de_bloque">

                        <div class="titulo_de_bloque" >
                            <h4><asp:Label ID="Label29" runat="server"  Text="Error"></asp:Label></h4>
                        </div>


                        <div class="contenido_de_bloque">
                
   
                
               
               <table cellpadding="0" align="center"  >
            <tr style="height: 20px">
            <td></td>
            </tr>
               
                <tr>
                    <td align="center">
                        <asp:Image ID="Image8" runat="server" ImageUrl="~/Styles/2015/img/mensaje_error.png" />
                    </td>
                </tr>
                <tr>
                    <td align="center">&nbsp;
                        </td>
                </tr>
                <tr>
                    <td align="center">
                        <h4><asp:Label ID="lblError2" runat="server" CssClass="texto" Font-Bold="True" meta:resourcekey="lblError2Resource1" 
                            Text="¡Tu Pedido no fue procesado!"></asp:Label></h4>
                    </td>
                </tr>
                <tr>
                    <td align="center">&nbsp;
                        </td>
                </tr>
                <tr>
                    <td align="center">

                    </td>
                </tr>
            <tr>
            <td align="center">
                <asp:Label ID="lblerror4" runat="server" 
                    Text="Por favor, verifique la información que está ingresando en la pasarela de pago" Font-Bold="True" 
                    meta:resourcekey="lblerror4Resource1"></asp:Label></td>
            </tr>
                <tr>
                    <td align="center">
                        </td>
                </tr>
                <tr>
                    <td align="center">
                        <asp:Label ID="lblerror5" runat="server" Font-Bold="True" meta:resourcekey="lblerror5Resource1" 
                            Text="Si el error continua, póngase en contacto con nuestro Call Center al teléfono (511) 716 7000"></asp:Label>
                        </td>
                </tr>
                <tr>
                    <td align="center">
                        </td>
                </tr>
                <tr>
                    <td align="center">&nbsp;
                        </td>
                </tr>
                <tr>
                    <td align="center" dir="ltr" valign="middle">
                        <asp:Button ID="btnPayment" runat="server" CssClass="boton_basico etiqueta_naranja_grande" Text="Volver a Pagar" />
                        <asp:Button ID="btnOrderEdit" runat="server" CssClass="boton_basico etiqueta_naranja_grande" Text="Editar Pedido" />
                    </td>
                </tr>
            </table>

            <br><br>


                </div>


                </div>
            </asp:Panel>    
                            </div>
                        </div>


                        <!-- Tab 10 Completado -->
                        <div class="tab_panel" id="contenido_tab10" runat="server" clientidmode="Static">
                            <div class="texto_centrado">

                <asp:Panel class="columna_ancho8 " id="div10OrderComplete" runat="server">
                <div class="bloque_basico color_de_bloque ">



                <div class="titulo_de_bloque" >
                    <h4><asp:Label ID="Label28" runat="server" Text="¡ El Proceso de compra se realizo satisfactoriamente !"></asp:Label></h4>
                </div>


                <div class="contenido_de_bloque" >
                    <div class="fila-ajustable ">
                    

                <div class="bloque_basico color_de_bloque" runat="server" visible="false" >
                <table width="100%" border="0" align="center" cellpadding="0" cellspacing="4">
                  <tr>
                    <td width="40%" align="right">
                    <asp:Label ID="lblAmount" runat="server" CssClass="texto_normal" Text="Sub Total:&nbsp;&nbsp;" meta:resourcekey="lblAmountResource1"></asp:Label>
                    </td>
                    <td width="60%" align="left">
                    <div class="controles-grupales">
                    <asp:TextBox ID="txtAmount" runat="server" CssClass="campo_texto_simple" Width="130px" ReadOnly="True" TabIndex="220" 
                     meta:resourcekey="txtAmountResource1"></asp:TextBox>
                    </div>
                    </td>
                  </tr>
                  <tr>
                    <td align="right">
                    <asp:Label ID="lblShipping" runat="server" CssClass="texto_normal" Text="Flete:&nbsp;&nbsp;" meta:resourcekey="lblShippingResource1"></asp:Label>
                    </td>
                    <td align="left" >
                    <div class="controles-grupales">
                    <asp:TextBox ID="txtShipping" runat="server" CssClass="campo_texto_simple" Width="130px" ReadOnly="True"  TabIndex="221" meta:resourcekey="txtShippingResource1"></asp:TextBox>
                    </div>
                    </td>
                  </tr>
                  <tr>
                    <td align="right">
                    <asp:Label ID="lblTax" runat="server" CssClass="texto_normal" Text="Impuesto:&nbsp;&nbsp;" meta:resourcekey="lblTaxResource1"></asp:Label>
                    </td>
                    <td align="left">
                    <div class="controles-grupales">
                    <asp:TextBox ID="txtTax" runat="server" CssClass="campo_texto_simple" Width="130px" ReadOnly="True"  TabIndex="222" meta:resourcekey="txtTaxResource1"></asp:TextBox>
                    </div>
                    </td>
                  </tr>
                  <tr>
                    <td align="right">
                    <asp:Label ID="lblTax0" runat="server" CssClass="texto_normal" Text="Total:&nbsp;&nbsp;" meta:resourcekey="lblTax0Resource1"></asp:Label>
                    </td>
                    <td align="left">
                    <div class="controles-grupales">
                    <asp:TextBox ID="txtTotal" runat="server" CssClass="campo_texto_simple" Width="130px" ReadOnly="True"  TabIndex="223" meta:resourcekey="txtTotalResource1"></asp:TextBox>
                    </div>
                    </td>
                  </tr>

                   <tr>
                    <td align="right">
                    <asp:Label ID="lblRetailVolume" runat="server" Text="BV:&nbsp;&nbsp;" meta:resourcekey="lblRetailVolumeResource1" Visible="False"></asp:Label>
                    </td>
                    <td align="left">
                    <div class="controles-grupales">
                    <asp:TextBox ID="txtRetailVolume" runat="server" Width="130px" ReadOnly="True"  TabIndex="224" Text="500" meta:resourcekey="txtRetailVolumeResource1" Visible="False"></asp:TextBox>
                    </div>
                    </td>
                  </tr>
                  <tr>
                   <td colspan="2" align="center"><br>
                   <asp:Label ID="lbPrice" runat="server" CssClass="texto_tablet" Font-Bold="True" Text="Precio expresado en dolares." ForeColor="#5b5b5b"></asp:Label> 
                   <br>
                   </td>
                  </tr>
                  <tr>
                  <td colspan="2" align="center">
                  
                  </td>
                  </tr>
 
                </table>
                </div>

                
                    <div class="columna_ancho12" runat="server" >
                    <br>
                    <table width="90%" border="0" align="center" cellpadding="0" cellspacing="0">
                    <tr>

                    <td align="center" >
                    <br>
                    <asp:Image ID="Image9" runat="server" ImageUrl="~/Styles/2015/img/icono_mensaje2.png"  />
                    <br><br>
                    <asp:Label ID="Label32" runat="server" Text="Su Número de pedido es:"></asp:Label>
                    <asp:Label ID="lbNewOrderID" runat="server"></asp:Label>
                    <br><br>
                    <asp:Label ID="Label33" runat="server" Text="¡Proceso Realizado Satisfactoriamente!"></asp:Label>
                    
                    </td>
                   
                    </tr>
                 
                    </table>
                    <br><br><br>
                    <table width="100%" border="0" align="center" cellpadding="5" cellspacing="0" >
                        <tr>       
                        <td align="center" >
                        </td>
                        </tr>
                    </table>
                    <br><br>
                  
                    </div>

                    </div>

                    </div>


                </div>
                </asp:Panel>

                            </div>
                        </div>



                     </div>

                     </div>

            </div>
            </div>
            </div>




            <!-- Resumen -->
            <div class="columna_ancho4" id="divShoppingCar" runat="server">
                <div class="bloque_basico color_de_bloque" >

                <div class="titulo_de_bloque" style="background-color:#797979; ">
                    <h4 style="padding-top:15px;padding-bottom:15px; "><asp:Label ID="lblBlockTitle2" runat="server" Text="Carrito de Compras" ></asp:Label></h4>
                </div>

                <div class="contenido_de_bloque" style="min-height: 624px; ">

                    <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" >
                        <tr>
                        <td align="center">
                        <asp:Button ID="btnChangeCustomer" runat="server" CssClass="boton_basico boton_nuevabusqueda" Text="Cambiar de cliente" TabIndex="62" onclick="btnChangeCustomer_Click"/>
                        <asp:Button ID="btnNewSearch" runat="server" CssClass="boton_basico boton_nuevabusqueda" Text="Nueva Búsqueda" TabIndex="63" onclick="btnNewSearch_Click"/>
                        </td>
                        </tr>
                    </table>

                <hr>
                    <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0" >
                        <tr>
                        <td width="24%" align="center">
                        <asp:Image ID="Image1" runat="server" ImageUrl="~/Styles/2015/img/user-photo.jpg" class="imagen_circular_foto_pedidos" style="border: 1px Solid #c4c4c4; "/>
                        </td>

                        <td width="76s%" align="left"> 
                        <div class="controles-grupales tooltip-top" data-tooltip="Código del cliente">
                        <asp:Label ID="lbCustomerID" runat="server" CssClass="campo_textodinamico_codigo_s"></asp:Label></div>
                        <div class="controles-grupales tooltip-top" data-tooltip="Nombre del cliente">
                        <asp:Label ID="lbCustomerName" runat="server" CssClass="campo_textodinamico_persona_s"></asp:Label></div>
                        </td>
                        </tr>

                        <tr>
                        <td colspan="2" align="center">
                            <asp:Button ID="btnShoppingCarEmpty" runat="server" CssClass="boton_basico etiqueta_celeste_grande3" Text="VACIAR CARRITO" TabIndex="63" onclick="btnShoppingCarEmpty_Click"/>
                        </td>
                        </tr>
                    </table>

                <hr>

                
                <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0">
                   <tr>
                    <td align="center"> <br>
                    <asp:Label ID="Label23" runat="server" Text="Contenido del Pedido" Font-Bold="true"></asp:Label><br><br>
                    </td>
                   </tr>
                </table>


                <!-- Carrito de compras vacio -->
                <div id="divShoppingCarEmpty" runat="server" clientidmode="Static">
                <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" style="min-height: 120px; ">
                   <tr>
                    <td align="center" valign="top"> 
                    
                    <asp:Image ID="imgShoppingCart" runat="server" ImageUrl="~/Styles/2015/img/icono_carritocompras.png" style="margin-right: 10px; " />
                    <br>
                    <h4><asp:Label ID="Label63" runat="server" Text="Carrito de compras vacio."  ></asp:Label>
                    </td>
                   </tr>
                </table>
                </div>

                <asp:Panel id="divShoppingCarItems" runat="server" ClientIDMode="Static">

                        <asp:DataList ID="dtlOrderLines" runat="server" RepeatColumns="1" 
                        ClientIDMode="Static" width="100%" RepeatDirection="Horizontal" 
                        onitemdatabound="dtlOrderLines_ItemDataBound">
                            <ItemTemplate>

                                <div class="boton_clientes_lista" style="border-left:8px solid #dadada; ">
                                    <table width="100%" border="0" align="center" cellpadding="4" cellspacing="0" >
                                    <tr>

                                    <td align="left"  width="6%">
                                    <asp:Image ID="imgProduct" runat="server" CssClass="producto_foto_adaptable" ImageUrl='<%# "~/Styles/images/Products/"+DataBinder.Eval(Container.DataItem, "ProductID")+"_100.png" %>'  />
                                    </td>

                                    <td align="left" width="60%">
                                    <asp:HiddenField ID="hdProductID" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "ProductID") %>' Visible="false" />
                                    <asp:HiddenField ID="hdOrderLineID" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "OrderLineID") %>' Visible="false" />
                                    <asp:HiddenField ID="hdGroupID" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "GroupID") %>' Visible="false" />
                                    <h5><asp:Label ID="lbOrderLineName" runat="server" Text='<%# DataBinder.Eval(Container.DataItem, "ProductName") %>' Font-Bold="true" CssClass="texto_en_tablet"></asp:Label></h5>
                                    
                                    
                                    <table width="70%" border="0" align="left" cellpadding="0" cellspacing="0" >
                                       <tr>
                                        <td align="center" width="18%"> 
                                        <div class="controles-grupales tooltip-top" data-tooltip="Reducir cantidad">
                                         <asp:ImageButton ID="btnOrderLineSubtract" runat="server" CssClass="efecto_zoom icono_adaptable_masmenos" 
                                         ImageUrl="~/Styles/2015/img/boton_menos_productos.png" TabIndex="64" 
                                         ValidationGroup="ValidateOrderLineQuantity" CommandArgument="-" onclick="btnOrderLineChange_Click" />
                                        </div>
                                        </td>

                                        <td align="center" width="64%"> 
                                        <div data-tooltip="Cantidad" class="tooltip-bottom" >
                                        <asp:TextBox ID="txtOrderLineQuantity" runat="server" ClientIDMode="Static" Text='<%# DataBinder.Eval(Container.DataItem, "Quantity") %>' MaxLength="3"
                                        CssClass="campo_textodinamico_gris_cantidad" placeholder="Cantidad "
                                        onKeyUp="$('input[name = \''+this.name.replace(this.id,'btnOrderLineEQ')+'\']').click();" ></asp:TextBox>
                                        </div>
                                        </td>

                                        <td align="center" width="18%">
                                        <div class="controles-grupales tooltip-top" data-tooltip="Aumentar cantidad">
                                        <asp:ImageButton ID="btnOrderLineAdd" runat="server" CssClass="efecto_zoom icono_adaptable_masmenos" 
                                        ImageUrl="~/Styles/2015/img/boton_mas_productos.png" TabIndex="65" 
                                        ValidationGroup="ValidateOrderLineQuantity" CommandArgument="+" onclick="btnOrderLineChange_Click" /> 
                                        </div>
                                        </td>

                                       </tr>
                                    </table>


                                    </td>

                                    <td align="right" valign="top" width="34%">
                                    <div class="controles-grupales tooltip-top" data-tooltip="Eliminar producto">
                                    <asp:ImageButton ID="btnOrderLineRemove" runat="server" CssClass="efecto_zoom icono_adaptable_masmenos" 
                                    ImageUrl="~/Styles/2015/img/boton_eliminar_productos.png" TabIndex="66" 
                                       CommandArgument="x" onclick="btnOrderLineChange_Click" />
                                    </div>

                                    <div style="display:none"><asp:ImageButton ID="btnOrderLineEQ" runat="server" CommandArgument="=" TabIndex="67" 
                                    onclick="btnOrderLineChange_Click" /></div>
                                    <br>
                                    <h5><asp:Label ID="lbOrderLineSubtotal" runat="server" Text='<%# string.Format("${0:###,##0.00}", DataBinder.Eval(Container.DataItem, "SubTotal")) %>' Font-Bold="true" 
                                    CssClass="texto_en_tablet"></asp:Label></h5>
                                    </td>

                                    </tr>
                                    </table>
                               </div>


                            </ItemTemplate>
                        </asp:DataList>

                </asp:Panel>
                <hr>

                <!-- Totales -->
                <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" style=" line-height:1.5;" >
                   <tr>
                    <td align="left" valign="top"> 
                    <asp:Label ID="lblShipCost" runat="server" Text="Costo de envío" Font-Bold="true"  ForeColor="#8f8f8f"></asp:Label>
                    </td>
                    <td align="right" valign="top"> 
                    <asp:Label ID="lbShipCost" runat="server" Text="0.00" Font-Bold="true" ForeColor="#8f8f8f"></asp:Label><br>
                    </td>
                   </tr>

                   <tr>
                    <td align="left" valign="top"> 
                    <asp:Label ID="Label1" runat="server" Text="Subtotal" Font-Bold="true"  ForeColor="#8f8f8f"></asp:Label>
                    </td>
                    <td align="right" valign="top"> 
                    <asp:Label ID="lbSubTotal" runat="server" Text="0.00" Font-Bold="True" ForeColor="#8F8F8F"></asp:Label><br>
                    </td>
                   </tr>

                   <tr>
                    <td align="left" valign="top"> 
                    <asp:Label ID="Label39" runat="server" Text="Impuestos" Font-Bold="true" ForeColor="#8f8f8f"></asp:Label>
                    </td>
                    <td align="right" valign="top"> 
                    <asp:Label ID="lbTaxAmt" runat="server" Text="0.00" Font-Bold="True" ForeColor="#8F8F8F"></asp:Label><br>
                    </td>
                   </tr>

                   <tr>
                    <td valign="top" colspan="2" > 
                    <hr>
                    </td>
                   </tr>

                   <tr>
                    <td align="left" valign="top"> 
                    <h4><asp:Label ID="lblTotal" runat="server" Text="Total a pagar" Font-Bold="true"></asp:Label></h4>
                    </td>
                    <td align="right" valign="top"> 
                    <h4><asp:Label ID="lbTotal" runat="server" Font-Bold="true"></asp:Label></h4>
                    </td>
                   </tr>
                </table> 
                 
                <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" >
                   <tr>
                    <td align="center">
                    <asp:Button ID="btnContinue" runat="server" CssClass="boton_basico etiqueta_naranja_grande3" Text="CONTINUAR" TabIndex="68"  OnClick="btnContinue_Click" /><br>
                    <asp:Button ID="btnContinueComplete" runat="server" CssClass="boton_basico etiqueta_celeste_grande3" Text="COMPLETAR PEDIDO" TabIndex="69"  OnClick="btnContinueComplete_Click" /><br>
                    <asp:Label ID="lbMessage" runat="server" CssClass="etiqueta etiqueta_azul" style="margin-top: 6px;" ></asp:Label><br>
                    </td>
                   </tr>
                </table>

                </div>

                </div>
            </div>





        </div>




            <!-- POPUP CONTENIDO DE PAQUETE -->
            <asp:HiddenField ID="hdProductContent" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpeProductContent" BehaviorID="mpeProductContent" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlProductContent" TargetControlID="hdProductContent" CancelControlID="lnkProductContentCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlProductContent" runat="server" ClientIDMode="Static" style="display:none; z-index: 9999 !important;">
            <asp:HiddenField ID="hdProductContentID" runat="server" Visible="false" />
            <table border="0" align="center" cellpadding="5" cellspacing="0" style="background-color: #00c261; padding:7px; border-radius:6px; width:90%; max-width:900px; min-width:800px;">
                <tr>
                <td align="center"><br>
                    <h4><asp:Label ID="Label62" runat="server" Text="Seleccione el contenido de su Paquete" ForeColor="#ffffff"></asp:Label></h4>
                    <asp:DataList ID="dtlProductsContent" runat="server" RepeatColumns="3" ClientIDMode="Static" RepeatDirection="Horizontal"
                            onitemdatabound="dtlProductsContent_ItemDataBound" style=" text-align:center;">
                        <ItemTemplate>
                            <div class="etiqueta" align="center" style="width:86%">

                            <asp:HiddenField ID="hdProductID" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "ProductID") %>' />
                            <asp:HiddenField ID="hdDescription" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "ProductName") %>' />
                            <asp:HiddenField ID="hdPrice" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "WholesalePrice") %>' />
                            <asp:HiddenField ID="hdWeight" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "Weight") %>' />
                            <asp:HiddenField ID="hdPV" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "WholesaleVolume") %>' />
                            <asp:HiddenField ID="hdCV" runat="server" Value='<%# DataBinder.Eval(Container.DataItem, "RetailVolume") %>' />

                            <asp:Image ID="imgProduct" runat="server" Width="100px"
                            ImageUrl='<%# "~/Styles/images/Products/"+DataBinder.Eval(Container.DataItem, "ProductID")+"_100.png" %>'
                            ToolTip='<%# "Producto: "+DataBinder.Eval(Container.DataItem, "ProductName") %>' />

                            <div class="margen_izquierda" data-toggle="tooltip" data-placement="right" title="Elegir la cantidad" placeholder="Elegir la cantidad" >
                            <div class="icono_caja_de_texto_espacio">
                            <span class="agregar_icono caja_de_texto_altura" style="color: #333333 !important;">Cantidad</span>
                            <asp:DropDownList ID="ddlQuantity" runat="server" CssClass="select5" TabIndex="6" >
                            </asp:DropDownList>
                            </div>
                            </div>


                            </div>
                        </ItemTemplate>
                    </asp:DataList>
                    </td>
                </tr>

                <tr style="height:120px;" align="center">
                <td>
                <hr />
                <br />
                <asp:LinkButton ID="lnkProductContentCancel" runat="server" ClientIDMode="Static" CssClass="boton_basico boton_cerrar2" Text="Cancel" style="margin-left:3px; " TabIndex="7" />
                <asp:LinkButton ID="lnkProductContentAdd" runat="server" ClientIDMode="Static" CssClass="boton_basico boton_guardar" Text="OK" style="margin-left:3px; " TabIndex="7" OnClick="lnkProductContentAdd_Click" ValidationGroup="ValidateOrderSave" />
                <br /><br />
                </td>
                </tr>


            </table>

            </asp:Panel>


            <!-- POPUP DESCARGAR TIPO DE PAGO EWALLET-EXTRALIFE -->
            <asp:HiddenField ID="hdPaymentTypeCollect" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpePaymentTypeCollect" BehaviorID="mpePaymentTypeCollect" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlPaymentTypeCollect" TargetControlID="hdPaymentTypeCollect" CancelControlID="lnkPaymentTypeCollectCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlPaymentTypeCollect" runat="server" ClientIDMode="Static" style="display:none; z-index: 99999 !important;">
            <asp:HiddenField ID="hdPaymentTypeCollect_PaymentID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeCollect_PaymentType" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeCollect_PaymentAmount" runat="server" Visible="false" />
            <table width="90%" border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px;
            box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">
                <tr>
                <td align="center" colspan="3" >
                    <h4 style="background-color: #27c266; min-height:64px;">
                    <br>
                    <asp:Label ID="Label19" runat="server" Text="Buscador de Créditos" ForeColor="#ffffff" Font-Bold="true"></asp:Label>
                    <br><br>
                    </h4>
                </td>
                </tr>

                <tr>
                <td colspan="3"><br></td>
                </tr>

                <tr>
                <td align="right" width="30%" >
                    <asp:Label ID="lblPaymentTypeCollect_CustomerID_Search" runat="server" Text="Código:" ForeColor="#333333"></asp:Label>
                </td>
                <td>
                    <asp:TextBox ID="txtPaymentTypeCollect_CustomerID" runat="server" ClientIDMode="Static" TabIndex="6" 
                    CssClass="campo_texto_simple_3_xl bajar_movil"></asp:TextBox>
                    <asp:RequiredFieldValidator ID="rfvPaymentTypeCollect_Search_CustomerID" runat="server" ControlToValidate="txtPaymentTypeCollect_CustomerID" ErrorMessage="*" Font-Bold="True" 
                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSearchPaymentTypeCollect"></asp:RequiredFieldValidator>
                </td>
                <td width="30%">
                    <asp:LinkButton ID="lnkPaymentTypeCollect_Search" runat="server" Text="Buscar" ClientIDMode="Static" OnClick="lnkPaymentTypeCollect_Search_Click" ValidationGroup="ValidateSearchPaymentTypeCollect" CssClass="boton_basico boton_nuevabusqueda" 
                     TabIndex="7" /><br>
                </td>


                <tr>
                <td align="center" colspan="3">
                    <asp:Label ID="lbPaymentTypeCollect_Message" runat="server" CssClass="etiqueta etiqueta_azul" ></asp:Label>
                </td>
                </tr>

                <tr>
                <td align="center" colspan="3">
                    <hr />
                    <br />

                    <h4><asp:Label ID="Label92" runat="server" Text="Origen de Créditos" ForeColor="#333333" Font-Bold="true"></asp:Label></h4>

                    <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" >
                    <tr>
                    <td align="right" width="49%">
                        <asp:Label ID="lblPaymentTypeCollect_CustomerID_Result" runat="server" Text="Código:" Font-Bold="true" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                        <asp:HiddenField ID="hdPaymentTypeCollect_CustomerID" runat="server" />
                        <asp:Label ID="lbPaymentTypeCollect_CustomerID" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    <tr>
                    <td align="right">
                        <asp:Label ID="lblPaymentTypeCollect_CustomerName_Result" runat="server" Text="Nombre:" Font-Bold="true" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                        <asp:Label ID="lbPaymentTypeCollect_CustomerName" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    <tr>
                    <td align="right">
                        <asp:Label ID="lblPaymentTypeCollect_UsedCredits" runat="server" Text="Créditos Requeridos:" Font-Bold="true" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                        <asp:Label ID="lbPaymentTypeCollect_UsedCredits" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    <tr>
                    <td align="right">
                        <asp:Label ID="lblPaymentTypeCollect_AvailableCredits" runat="server" Text="Créditos Disponibles:" Font-Bold="true" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                        <asp:Label ID="lbPaymentTypeCollect_AvailableCredits" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>
                    </table>


                </td>
                </tr>

                <tr style="height:120px;" align="center">
                <td colspan="3">
                <hr />
                <br />
                <asp:LinkButton ID="lnkPaymentTypeCollectCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" TabIndex="7"  />
                <asp:LinkButton ID="lnkPaymentTypeCollectOk" runat="server" Text="Descargar Créditos" ClientIDMode="Static" 
                CssClass="boton_basico boton_descargar" style="margin-left:10px; " TabIndex="7"  
                OnClick="lnkPaymentTypeCollectOk_Click" ValidationGroup="ValidatePaymentTypeCollect" />

                <br /><br />
                </td>
                </tr>
            </table>

            </asp:Panel>


            <!-- POPUP REMOVER TIPO DE PAGO EWALLET-EXTRALIFE -->
            <asp:HiddenField ID="hdPaymentTypeRemove" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpePaymentTypeRemove" BehaviorID="mpePaymentTypeRemove" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlPaymentTypeRemove" TargetControlID="hdPaymentTypeRemove" CancelControlID="lnkPaymentTypeRemoveCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlPaymentTypeRemove" runat="server" ClientIDMode="Static" style="display:none; z-index: 99999 !important; min-width: 350px;">
            <asp:HiddenField ID="hdPaymentTypeRemove_PaymentID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeRemove_PaymentType" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeRemove_PaymentAmount" runat="server" Visible="false" />
            <table width="60%" border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px; 
            box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">
                <tr>
                <td align="center" >
                    <h4 style="background-color: #27c266; min-height:64px;">
                    <br>
                    <asp:Label ID="Label22" runat="server" Text="Origen de Créditos" ForeColor="#ffffff" Font-Bold="true"></asp:Label>
                    <br><br>
                    </h4>

                </td>
                </tr>

                <tr>
                <td align="right">

                    <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" >
                    <tr>
                    <td align="right" width="49%">
                    <asp:Label ID="lblPaymentTypeRemove_CustomerID_Result" runat="server" Text="Código:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:HiddenField ID="hdPaymentTypeRemove_CustomerID" runat="server" />
                    <asp:Label ID="lbPaymentTypeRemove_CustomerID" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    <tr>
                    <td align="right">
                    <asp:Label ID="lblPaymentTypeRemove_CustomerName_Result" runat="server" Text="Nombre:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:Label ID="lbPaymentTypeRemove_CustomerName" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    <tr>
                    <td align="right">
                    <asp:Label ID="lblPaymentTypeRemove_UsedCredits" runat="server" Text="Créditos Descargados:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:Label ID="lbPaymentTypeRemove_UsedCredits" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    <tr>
                    <td align="right">
                    <asp:Label ID="lblPaymentTypeRemove_AvailableCredits" runat="server" Text="Créditos Disponibles:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:Label ID="lbPaymentTypeRemove_AvailableCredits" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>
                    </table>
                 
                </td>
                </tr>


                <tr style="height:120px;" align="center">
                <td >
                <hr />
                <br />
                <asp:LinkButton ID="lnkPaymentTypeRemoveCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" style="margin-left:3px; " TabIndex="7" />
                <asp:LinkButton ID="lnkPaymentTypeRemoveOk" runat="server" Text="Retornar Créditos" ClientIDMode="Static" 
                CssClass="boton_basico boton_descargar" style="margin-left:3px; " TabIndex="7" OnClick="lnkPaymentTypeRemoveOk_Click" ValidationGroup="ValidatePaymentTypeRemove" />
                </td>
                </tr>
            </table>

            </asp:Panel>

            <!-- POPUP DESCARGAR TIPO DE PAGO CREDIT NOTE -->
            <asp:HiddenField ID="hdPaymentTypeCollect_CreditNote" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpePaymentTypeCollect_CreditNote" BehaviorID="mpePaymentTypeCollect_CreditNote" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlPaymentTypeCollect_CreditNote" TargetControlID="hdPaymentTypeCollect_CreditNote" CancelControlID="lnkPaymentTypeCollect_CreditNoteCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlPaymentTypeCollect_CreditNote" runat="server" ClientIDMode="Static" style="display:none; z-index: 99999 !important;">
            <asp:HiddenField ID="hdPaymentTypeCollect_CreditNote_PaymentID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeCollect_CreditNote_PaymentType" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeCollect_CreditNote_PaymentAmount" runat="server" Visible="false" />
            <table width="90%" border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px; box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">
                <tr>
                <td align="center" colspan="3" >
                    <h4 style="background-color: #27c266; min-height:64px;">
                    <br>
                    <asp:Label ID="Label94" runat="server" Text="Notas de Crédito Disponibles" ForeColor="#ffffff" Font-Bold="true"></asp:Label>
                    <br><br>
                    </h4>
                </td>
                </tr>

                <tr>
                <td colspan="3"><br></td>
                </tr>

                <tr>
                <td align="right" width="25%" >
                    <asp:Label ID="lblPaymentTypeCollect_CreditNote_CustomerID_Search" runat="server" Text="Nota de Crédito:" ForeColor="#333333"></asp:Label>
                </td>
                <td colspan="2">
                    <asp:DropDownList ID="ddlPaymentTypeCollect_CreditNote_ID" runat="server" style="width: 480px !important;" CssClass="campo_texto_select_almacen2" TabIndex="58" placeholder="Almacén">
                    </asp:DropDownList>
<%--                    <asp:TextBox ID="txtPaymentTypeCollect_CreditNote_CustomerID" runat="server" ClientIDMode="Static" TabIndex="6" 
                    CssClass="campo_texto_simple_3_xl bajar_movil"></asp:TextBox>--%>
                    <asp:RequiredFieldValidator ID="rfvPaymentTypeCollect_CreditNote_Search_ID" runat="server" ControlToValidate="ddlPaymentTypeCollect_CreditNote_ID" ErrorMessage="*" Font-Bold="True" 
                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateSearchPaymentTypeCollect_CreditNote"></asp:RequiredFieldValidator>
                    &nbsp;&nbsp;&nbsp;
                </td>
<%--                <td width="30%">
                    <asp:LinkButton ID="lnkPaymentTypeCollect_CreditNote_Search" runat="server" Text="Buscar" ClientIDMode="Static" OnClick="lnkPaymentTypeCollect_CreditNote_Search_Click" ValidationGroup="ValidateSearchPaymentTypeCollect_CreditNote" CssClass="boton_basico boton_nuevabusqueda" 
                     TabIndex="7" /><br>
                </td>--%>


                <tr>
                <td align="center" colspan="3">
                    <asp:Label ID="lbPaymentTypeCollect_CreditNote_Message" runat="server" CssClass="etiqueta etiqueta_azul" ></asp:Label>
                </td>
                </tr>

                <tr style="height:120px;" align="center">
                <td colspan="3">
                <hr />
                <br />
                <asp:LinkButton ID="lnkPaymentTypeCollect_CreditNoteCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" TabIndex="7"  />
                <asp:LinkButton ID="lnkPaymentTypeCollect_CreditNoteOk" runat="server" Text="Vincular Nota de Crédito" ClientIDMode="Static" 
                CssClass="boton_basico boton_descargar" style="margin-left:10px; " TabIndex="7"  
                OnClick="lnkPaymentTypeCollect_CreditNoteOk_Click" ValidationGroup="ValidatePaymentTypeCollect_CreditNote" />

                <br /><br />
                </td>
                </tr>
            </table>

            </asp:Panel>

            <!-- POPUP REMOVER TIPO DE PAGO CREDIT NOTE -->
            <asp:HiddenField ID="hdPaymentTypeRemove_CreditNote" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpePaymentTypeRemove_CreditNote" BehaviorID="mpePaymentTypeRemove_CreditNote" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlPaymentTypeRemove_CreditNote" TargetControlID="hdPaymentTypeRemove_CreditNote" CancelControlID="lnkPaymentTypeRemove_CreditNoteCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlPaymentTypeRemove_CreditNote" runat="server" ClientIDMode="Static" style="display:none; z-index: 99999 !important; min-width: 350px;">
            <asp:HiddenField ID="hdPaymentTypeRemove_CreditNote_ID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeRemove_CreditNote_PaymentID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeRemove_CreditNote_PaymentType" runat="server" Visible="false" />
            <asp:HiddenField ID="hdPaymentTypeRemove_CreditNote_PaymentAmount" runat="server" Visible="false" />
            <table width="60%" border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px; 
            box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">
                <tr>
                <td align="center" >
                    <h4 style="background-color: #27c266; min-height:64px;">
                    <br>
                    <asp:Label ID="Label96" runat="server" Text="Notas de Crédito" ForeColor="#ffffff" Font-Bold="true"></asp:Label>
                    <br><br>
                    </h4>

                </td>
                </tr>

                <tr>
                <td align="right">

                    <table width="100%" border="0" align="center" cellpadding="0" cellspacing="0" >
                    <tr>
                    <td align="right" width="40%">
                    <asp:Label ID="lblPaymentTypeRemove_CreditNote_Document_Result" runat="server" Text="Documento:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:Label ID="lbPaymentTypeRemove_CreditNote_Document" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>
                    <tr>
                    <td align="right" width="40%">
                    <asp:Label ID="lblPaymentTypeRemove_CreditNote_Date_Result" runat="server" Text="Fecha:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:Label ID="lbPaymentTypeRemove_CreditNote_Date" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>
                    <tr>
                    <td align="right" width="40%">
                    <asp:Label ID="lblPaymentTypeRemove_CreditNote_Amount_Result" runat="server" Text="Importe:" ForeColor="#333333"></asp:Label>
                    </td>
                    <td width="2%"></td>
                    <td>
                    <asp:Label ID="lbPaymentTypeRemove_CreditNote_Amount" runat="server" ForeColor="#333333"></asp:Label>
                    </td>
                    </tr>

                    </table>
                 
                </td>
                </tr>


                <tr style="height:120px;" align="center">
                <td >
                <hr />
                <br />
                <asp:LinkButton ID="lnkPaymentTypeRemove_CreditNoteCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" style="margin-left:3px; " TabIndex="7" />
                <asp:LinkButton ID="lnkPaymentTypeRemove_CreditNoteOk" runat="server" Text="Desvincular Nota de Crédito" ClientIDMode="Static" 
                CssClass="boton_basico boton_descargar" style="margin-left:3px; " TabIndex="7" OnClick="lnkPaymentTypeRemove_CreditNoteOk_Click" ValidationGroup="ValidatePaymentTypeRemove_CreditNote" />
                </td>
                </tr>
            </table>

            </asp:Panel>

            <!-- POPUP ANULAR PEDIDO -->
            <asp:HiddenField ID="hdCancelOrder" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpeCancelOrder" BehaviorID="mpeCancelOrder" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlCancelOrder" TargetControlID="hdCancelOrder" CancelControlID="lnkCancelOrderCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlCancelOrder" runat="server" ClientIDMode="Static" 
            style="display:none; z-index: 99999 !important; width:90%; max-width:700px; line-height:1.5;">
            <asp:HiddenField ID="hdCancelOrder_PaymentID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdCancelOrder_PaymentType" runat="server" Visible="false" />
            <asp:HiddenField ID="hdCancelOrder_PaymentAmount" runat="server" Visible="false" />
            <table border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px; 
                width:100%; 
            box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">

                <tr>
                <td align="center" >
                    <h4 style="background-color: #27c266; min-height:64px;">
                    <br><asp:Label ID="Label21" runat="server" Text="Desea anular este pedido?" ForeColor="#ffffff" Font-Bold="true">
                    </asp:Label><br><br></h4>

                </td>
                </tr>

                <tr>
                <td align="center" style="padding:10px;">

                    <br>
                    <asp:Label ID="Label20" runat="server" Text="Nota: Si el pago fue realizado con Créditos Ewallet o Créditos Extralife, <br>al proceder con la anulación estos créditos serán retornados al titular." ForeColor="#333333" ></asp:Label>
                    <br><br>

                </td>
                </tr>

                <tr style="height:120px;" align="center">
                <td >

                <asp:LinkButton ID="lnkCancelOrderCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" style="margin-left:3px; " TabIndex="7" />
                <asp:LinkButton ID="lnkCancelOrderOk" runat="server" Text="Anular Pedido" ClientIDMode="Static" 
                CssClass="boton_basico boton_anular2" style="margin-left:3px; " TabIndex="7" OnClick="lnkCancelOrderOk_Click" ValidationGroup="ValidateCancelOrder" />
                <br><br><br>
                </td>
                </tr>
            </table>

            </asp:Panel>


            <!-- POPUP CAMBIAR ALMACEN -->
            <asp:HiddenField ID="hdChangeWarehouse" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpeChangeWarehouse" BehaviorID="mpeChangeWarehouse" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlChangeWarehouse" TargetControlID="hdChangeWarehouse" CancelControlID="lnkChangeWarehouseCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlChangeWarehouse" runat="server" ClientIDMode="Static" style="display:none; z-index: 99999 !important;">
            <asp:HiddenField ID="hdChangeWarehouse_PaymentID" runat="server" Visible="false" />
            <asp:HiddenField ID="hdChangeWarehouse_PaymentType" runat="server" Visible="false" />
            <asp:HiddenField ID="hdChangeWarehouse_PaymentAmount" runat="server" Visible="false" />
            <table border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px; width:520px; 
            box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">

                <tr>
                <td align="center" >
                    <h4 style="background-color: #27c266; min-height:64px;">
                    <br><asp:Label ID="Label95" runat="server" Text="Seleccione el Nuevo Almacén" ForeColor="#ffffff" Font-Bold="true"></asp:Label><br><br></h4>

                </td>
                </tr>

                <tr>
                <td align="center">

                    <div data-tooltip="Seleccione el nuevo almacén" class="tooltip-bottom" >
                    <asp:DropDownList ID="ddlChangeWarehouse" runat="server" CssClass="campo_texto_select_almacen2" TabIndex="58" placeholder="Almacén">
                    </asp:DropDownList>
                    </div>

                </td>
                </tr>

                <tr style="height:150px;" align="center">
                <td >
                <br>
                <asp:LinkButton ID="lnkChangeWarehouseCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" style="margin-left:3px; " TabIndex="7" />
                <asp:LinkButton ID="lnkChangeWarehouseOk" runat="server" Text="Cambiar Almacén" ClientIDMode="Static" 
                CssClass="boton_basico boton_anular2" style="margin-left:3px; " TabIndex="7" OnClick="lnkChangeWarehouseOk_Click" ValidationGroup="ValidateChangeWarehouse" />
                <br><br><br>
                </td>
                </tr>
            </table>

            </asp:Panel>


           <!-- POPUP ENVIAR EMAIL - DOCUMENTO ELECTRONICO-->
            <asp:HiddenField ID="hdEmail_ElectronicDocument" runat="server" ClientIDMode="Static" />
            <asp:ModalPopupExtender ID="mpeEmail_ElectronicDocument" BehaviorID="mpeEmail_ElectronicDocument" runat="server" ClientIDMode="Static" BackgroundCssClass="modalBackground" 
                PopupControlID="pnlEmail_ElectronicDocument" TargetControlID="hdEmail_ElectronicDocument" CancelControlID="lnkEmail_ElectronicDocumentCancel" >
            </asp:ModalPopupExtender>

            <asp:Panel ID="pnlEmail_ElectronicDocument" runat="server" ClientIDMode="Static" 
            style="display:none; z-index: 99999 !important; width:98%; max-width:800px;">

            <table width="98%" border="0" align="center" cellpadding="0" cellspacing="0" style="background-color: #ffffff; padding:0px; border-radius:6px;
            box-shadow: 0px 3px 15px rgba(0,0,0,0.5) !important;">
                <tr>
                <td align="center" colspan="3" >
                    <h4 style="background-color: #27c266; min-height:60px; line-height:1.5">
                    <br>
                    <asp:Label ID="lblEmail_ElectronicDocument_Title" runat="server" Text="DOCUMENTO DIGITAL" ForeColor="#ffffff" Font-Bold="true"></asp:Label>
                    <br><br>
                    </h4>
                </td>
                </tr>

                <tr>
                <td colspan="3">


                    <table width="50%" border="0" align="center" cellpadding="0" cellspacing="0"  >
                    <tr>
                    <td align="center" >
                    <div style="width: 100%; overflow-y: scroll;" class="altura_scroll">                         
                    
                    <div style="width:150mm; height:150mm; background:#ffffff; /*  border: 1px solid #000;*/">                                                 
                    <asp:Literal ID="ltEmail_ElectronicDocument" runat="server"></asp:Literal>
                    </div> 
                                                                       
                    </div>
                    </td>
                    </tr>
                    </table>

                    <hr>
                </td>
                </tr>

                <tr>
                <td colspan="3" align="center">

                    <asp:Label ID="Label97" runat="server" Text="Ingresar Correo" Font-Bold="true"></asp:Label>
                    <asp:TextBox ID="txtPopupEmail_ElectronicDocument_Email" runat="server" ClientIDMode="Static" class="campo_texto_simple" 
                    style="background:#ffffff!important; " placeholder="correo@ejemplo.com" ></asp:TextBox>
                    <asp:RequiredFieldValidator ID="rfvPopupEmail_ElectronicDocument_Email" runat="server" ControlToValidate="txtPopupEmail_ElectronicDocument_Email" ErrorMessage="*" Font-Bold="True" 
                    ForeColor="Red" SetFocusOnError="True" ValidationGroup="ValidateEmail_ElectronicDocument"></asp:RequiredFieldValidator>

                </td>
                </tr>


                <tr style="height:120px;" align="center">
                <td colspan="3">
                <hr />
                <br>
                <asp:LinkButton ID="lnkEmail_ElectronicDocumentCancel" runat="server" Text="Cancel" ClientIDMode="Static" 
                CssClass="boton_basico boton_cerrar2" TabIndex="7" />
                <asp:LinkButton ID="lnkEmail_ElectronicDocumentOk" runat="server" Text="Enviar Email" ClientIDMode="Static" 
                CssClass="boton_basico boton_descargar" style="margin-left:10px; " TabIndex="7" 
                OnClick="lnkEmail_ElectronicDocumentOk_Click" ValidationGroup="ValidateEmail_ElectronicDocument" />

                <br><br>
                </td>
                </tr>
            </table>

            </asp:Panel>


</ContentTemplate>
<%--<Triggers>
<asp:AsyncPostBackTrigger ControlID="btnProductAdd" EventName="Clic" />
</Triggers>--%>
</asp:UpdatePanel>

