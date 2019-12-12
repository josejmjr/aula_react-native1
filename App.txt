/**
 * Sample React Native App
 * https://github.com/facebook/react-native
 *
 * @format
 * @flow
 */

import React, {Component} from 'react';
import {StyleSheet, View, Text, FlatList, TextInput, Button} from 'react-native';

type Props = {};

export default class App extends Component<Props>{

  constructor(props){

    super(props)
    this.state={
      text: "",
      pessoas: [] 
    }

    this.inserirPessoa = this.inserirPessoa.bind(this)

  }

  renderItem(obj){
    return(
      <Text style={styles.item}>{obj.item.nome}</Text>
    )
  }

  inserirPessoa(){
    let newPessoa = {
      key: this.state.pessoas.length.toString(),
      nome: this.state.text,
      //done: false
    }

    let pessoas = this.state.pessoas;
    pessoas.push(newPessoa)
    this.setState({pessoas})

    let text = ""
    this.setState({text})

  }

  render(){
    return (
      <View style={styles.container}>
        <View style={styles.inputView}>
          <TextInput placeholder="Insira seu nome" style={styles.input} onChangeText={(text)=>{this.setState({text})}} value={this.state.text} />
          <Button onPress={this.inserirPessoa} title="Inserir"/>
        </View>
        <FlatList style={styles.lista} data={this.state.pessoas} renderItem={this.renderItem} extraData={this.state}/>    
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container:{
    flex: 1,
    justifyContent: 'center',
    backgroundColor: '#F5FCFF'
  },

  lista: {
    marginTop:25
  },

  item:{
    paddingTop: 20,
    paddingBottom: 20,
    backgroundColor: '#E4EBEE',
    fontSize: 18,
    marginBottom: 5,
    textAlign: 'center'
  },

  inputView:{
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
    margin: 5,
  },

  
  input:{
    backgroundColor: '#fff',
    borderColor: '#ccc',
    borderWidth: 3,
    padding: 5,
    margin: 5,
    flex: 1
  }
});


