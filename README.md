# exer4

import React from 'react';
import {Text, Button, View, ScrollView} from 'react-native';
import axios from 'axios';

function App(): JSX.Element {
  const [dados, setDados] = React.useState([]);
  return (
    <View>
      <Button
        title="Buscar"
        onPress={async () => {
          const {data} = await axios.get(
            'https://sci01-ter-jne.ufca.edu.br/cppgi/api/avaliacoes/2370/1/TODAS',
          );
          setDados(data);
        }}
      />
      <ScrollView>
        {dados.map(item => {
          return <Text key={item.id}>{item.titulo}</Text>;
        })}
      </ScrollView>
    </View>
  );
}

export default App;
