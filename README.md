# meatmore
Slides and example code on the training Angular Advanced for Meat and More, Aalter, BE. June 2020

## Links from the training 
- Repository met voorbeeldcode: https://github.com/PeterKassenaar/AngularAdvanced.
- Repo met RxJS voorbeelden: https://github.com/PeterKassenaar/ng-rxjs-operators.
- Repo met Testing voorbeelden: https://github.com/PeterKassenaar/ng-testing
- Repo met Monorepo: https://github.com/PeterKassenaar/ng-monorepo.

## More links
- Cancelling RxJS - requests. Er was vroeger een .cancel() operator, maar die bestaat in nieuwe RxJS-versies niet meer. Probeer dit artikel : https://medium.com/the-geeks-of-creately/cancelling-observables-rxjs-f4cf28c3b633
- HTTP Interceptor article: https://alligator.io/angular/testing-http-interceptors/
- Retry failed http requests after some time: https://medium.com/angular-in-depth/retry-failed-http-requests-in-angular-f5959d486294

## Example

### Fetching Country data: Template
```html
<button (click)="getCountries()" class="btn btn-primary">Get countries</button>
<ul class="list-group">
    <li class="list-group-item" *ngFor="let country of country$ | async">
        <img src="{{ country.flag}}" alt="" width="80">
        <p>{{ country.name }}</p>
        <p>{{ country.capital }}</p>
    </li>
</ul>
```

### Fetching Country data: Class

```typescript
country$: Observable<any[]>;
getCountries() {
		this.country$ = this.cityService.getCountries();
    }
```
### Fetching Country data: Service
```typescript
 url = 'https://restcountries.eu/rest/v2/all';
 urlName = 'https://restcountries.eu/rest/v2/name/'
...
getCountriesAll() :Observable<any>{
        return this.http.get<any[]>(this.url)
    }
    getCountriesName() :Observable<any>{
        return this.http.get<any[]>(this.urlName + 'BEL')
    }
```
