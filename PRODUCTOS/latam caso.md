# ✈️ Caso LATAM — Sabre y Forwarding a Banco Internacional

> [!INFO] Caso Especial
> Notas del caso particular de **LATAM** con **Sabre** y **Red Datafast/Austro/Medianet**. Manejo especial del campo `installment`.

---

## 🔑 Problema

**LATAM** utiliza **Sabre** como sistema de reservas, y este siempre envía `installment = 1`.

Para las redes **Datafast**, **Austro** y **Medianet**, el valor correcto de `installment` debería ser **0** (pago único, sin cuotas).

---

## 🔄 Solución Implementada

Se realizó un cambio en **PlacetoPay (P2P)** para hacer una **conversión**:

| Valor Recibido | Valor Convertido | Significado |
|----------------|------------------|-------------|
| `installment = 1` | `installment = 0` | Pago único (sin cuotas) |

> [!WARNING]
> Esta conversión evita que se rompa el flujo de pago. Sin ella, el sistema interpretaría el pago como una cuota de un plan de financiamiento.

---

## 🔗 Forwarding a Banco Internacional

**LATAM** realiza el proceso como siempre lo maneja, pero hace **FORWARDING** a **Banco Internacional**.

### Diagrama del Flujo

> Ver archivo visual de referencia:
> ![[Pasted image 20260825151755.png]]

### Lo que debería enviar LATAM:

> ![[Pasted image 20260825151910.png]]

### Envío final de LATAM:

> ![[Pasted image 20260825151949.png]]

---

## 📌 Notas

- Este caso aplica solo para comercios que usen **Sabre** como sistema de reservas
- Las redes involucradas son: **Datafast**, **Austro** y **Medianet**
- La solución está implementada a nivel de **P2P** (conversión automática)
- **Relacionado:** [[PRODUCTOS/Dispersión/DISPERSIÓN _1|Dispersión]], [[PRODUCTOS/API/API|API]]
