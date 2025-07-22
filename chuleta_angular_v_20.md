# 🧠 Chuleta Angular v20

> Pequeña chuletilla con lo esencial de los tutoriales de Angular v20

---

## 🧱 1. Componentes

**Crear un componente standalone:**

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-hello',
  standalone: true,
  template: `<p>Hello, {{name}}!</p>`,
})
export class HelloComponent {
  name = 'Angular';
}
```

**Actualizar datos (reactividad):**

```ts
import { signal } from '@angular/core';

name = signal('Angular');
this.name.set('Ng20');
```

---

## 🔁 2. Composición de Componentes

**Usar un componente hijo en el padre:**

```ts
imports: [ChildComponent]
```

**Pasar datos al hijo con **``**:**

```ts
@Input() data: string = '';
```

**Emitir eventos al padre con **``**:**

```ts
@Output() clicked = output<string>();
```

---

## 🥮 3. Control Flow (@if, @for)

**@if:**

```html
@if (user()) {
  <p>Hola {{ user().name }}</p>
} @else {
  <p>Inicia sesión</p>
}
```

**@for:**

```html
@for (item of items(); track item) {
  <p>{{ item }}</p>
}
```

---

## 🔗 4. Property Binding

```html
<img [src]="imageUrl" [alt]="description" />
```

---

## 🎯 5. Event Handling

```html
<button (click)="doSomething()">Haz algo</button>
```

---

## 🛄 6. @Input y @Output

**En el hijo:**

```ts
@Input() title: string;
@Output() selected = output<string>();
```

**En el padre:**

```html
<app-hijo [title]="titulo" (selected)="onSelect($event)" />
```

---

## 💤 7. Deferrable Views

```html
@defer {
  <p>Contenido diferido</p>
} @placeholder {
  <p>Cargando...</p>
}
```

---

## 🖼️ 8. Optimización de Imágenes (NgOptimizedImage)

```html
<img ngSrc="/assets/logo.svg" width="100" height="100" />
<img ngSrc="img.jpg" fill />
```

> Asegúrate de importar `NgOptimizedImage` y usar `position: relative` para contenedores con `fill`.

---

## 🧭 9. Routing

**Definir rutas (app.routes.ts):**

```ts
import { Routes } from '@angular/router';
import { HomeComponent } from './home';
import { UserComponent } from './user';

export const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'user', component: UserComponent },
];
```

**Usar RouterOutlet (app.ts):**

```html
<router-outlet />
```

---

## 🦾 10. Formularios

### 🔸 Template-driven:

```html
<form #f="ngForm" (ngSubmit)="onSubmit(f)">
  <input name="nombre" ngModel required />
</form>
```

### 🔸 Reactivos:

```ts
form = new FormGroup({
  nombre: new FormControl('', Validators.required)
});
```

```html
<form [formGroup]="form" (ngSubmit)="submit()">
  <input formControlName="nombre" />
</form>
```

---

## ✅ 11. Validación

**Template:**

```html
<input ngModel required #c="ngModel" />
<p *ngIf="c.invalid && c.touched">Campo obligatorio</p>
```

**Reactivo:**

```ts
Validators.minLength(3)
```

---

## 🛠️ 12. Servicios Inyectables

**Crear servicio:**

```ts
@Injectable({ providedIn: 'root' })
export class MyService {
  getData() { return '🎉'; }
}
```

**Inyectar servicio:**

```ts
constructor(private myService: MyService) {}
```

**O usando **``**:**

```ts
myService = inject(MyService);
```

---

## 🤪 13. Pipes (Tuberías)

**Uso de pipe:**

```html
<p>{{ fecha | date:'longDate' }}</p>
```

**Crear una pipe personalizada:**

```ts
@Pipe({ name: 'mayuscula', standalone: true })
export class MayusculaPipe implements PipeTransform {
  transform(value: string): string {
    return value.toUpperCase();
  }
}
```

---

🎉 ¡Listo! Ya tienes tu resumen impreso de Angular v20.

