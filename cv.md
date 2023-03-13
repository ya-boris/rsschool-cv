# Boris Yarmulnik

Innovative Front-End Developer with 2 years experience building and maintaining responsive websites in the recruiting industry.

Proficient in HTML, CSS, jQuery, JavaScript and React plus modern libraries and frameworks.

Passionate about usability and possess working knowledge of Adobe Photoshop & Sketch.

## Contacts
344019, Russia, Rostov-on-Don

<boris.yarmoulnik@gmail.com>

+7 (938) 15-666-51

## Project
null

## Code example
```
import {useState, useEffect, useContext} from 'react';
import {useHistory} from 'react-router-dom';
import {FireBaseContext} from '../../../../context/firebaseContext';
import {PokemonContext} from '../../../../context/pokemonContext';

import PokemonCard from '../../../../components/PokemonCard';

import s from './style.module.css';

const StartPage = () => {
  const history = useHistory();
  const firebase = useContext(FireBaseContext);
  const pokemonsContext = useContext(PokemonContext);

  const [pokemons, setPokemons] = useState({});

  const getPokemons = async () => {
    const response = await firebase.getPokemonsOnce();
    setPokemons(response);
  }

  useEffect(() => {
    firebase.getPokemonSocket((pokemons) => {
      setPokemons(pokemons);
    });

    return () => firebase.offPokemonSocket();
  }, []);

  const handleChangeSelected = (key) => {
    const pokemon = {...pokemons[key]};
    pokemonsContext.onSelectedPokemons(key, pokemon);
    setPokemons(prevState => ({
      ...prevState,
      [key]: {
        ...prevState[key],
        isSelected: !prevState[key].isSelected
      }
    }))
  }

  const handleAddPokemon = () => {
    const data = DATA;
    firebase.addPokemon(data, async () => {
      await getPokemons();
    });
  }

  const handleStartGameClick = () => {
    history.push('/game/board');
  }

  return (
    <>
      <div className={s.buttonWrap} align="center">
        <button onClick={handleAddPokemon} className={s.buttonNew}>Add new 🐥</button>
        <button onClick={handleStartGameClick} className={s.buttonStart} disabled={Object.keys(pokemonsContext.pokemons).length < 5}>Start game 🚀</button>
      </div>
      <div className={s.flex}>
        {
          Object.entries(pokemons).map(([key, {name, img, id, type, values, isSelected}]) => <PokemonCard
            className={s.card}
            key={key}
            id={id}
            name={name}
            img={img}
            type={type}
            values={values}
            isActive={true}
            isSelected = {isSelected}
            handleChangeSelected={() => {
              if (Object.keys(pokemonsContext.pokemons).length < 5 || isSelected) {
                handleChangeSelected(key);
              }

            }}
          />)
        }
      </div>
    </>
  )
}

export default StartPage;
```

## Education
**Bachelor's Degree in Computer Science, IUBIP**

2010

## Employment history

**Front-End Developer, ABC Systems, Rostov-on-Don**

2019 — 2020
  - Creating new features;
  - Recommending solutions;
  - Performing bug fixes.

**Front-End Developer, XYZ Systems, Rostov-on-Don**

2018 — 2019
  - Creating new features;
  - Recommending solutions;
  - Performing bug fixes.

**Front-End Developer, QWERTY Systems, Rostov-on-Don**

2017 — 2018
  - Creating new features;
  - Recommending solutions;
  - Performing bug fixes.

## Skills
  - HTML, CSS, JavaScript;
  - React, Redux, Angular, Jquery;
  - Adobe Photoshop;
  - Highly organized;
  - Attention to detail;
  - Clear communication;
  - Innovative problem-solving.

## Courses

**Udemy — JavaScript. The Complete Guide**

May 2020 — August 2020

## English

Good B2.